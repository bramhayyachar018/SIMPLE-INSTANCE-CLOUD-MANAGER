# SIMPLE-INSTANCE-CLOUD-MANAGER
class CloudInstance:
    def __init__(self, instance_id, status='stopped'):
        self.instance_id = instance_id
        self.status = status

    def launch(self):
        self.status = 'running'

    def stop(self):
        self.status = 'stopped'

    def update(self, new_instance_id):
        self.instance_id = new_instance_id

    def get_status(self):
        return self.status


class InstanceManager:
    def __init__(self):
        self.instances = {}

    def create_instance(self, instance_id):
        if instance_id in self.instances:
            raise ValueError(f"Instance {instance_id} already exists.")
        instance = CloudInstance(instance_id)
        self.instances[instance_id] = instance
        return instance

    def launch_instance(self, instance_id):
        instance = self.instances.get(instance_id)
        if not instance:
            raise ValueError(f"Instance {instance_id} not found.")
        instance.launch()

    def monitor_instance(self, instance_id):
        instance = self.instances.get(instance_id)
        if not instance:
            raise ValueError(f"Instance {instance_id} not found.")
        return instance.get_status()

    def update_instance(self, instance_id, new_instance_id):
        instance = self.instances.get(instance_id)
        if not instance:
            raise ValueError(f"Instance {instance_id} not found.")
        instance.update(new_instance_id)
        self.instances[new_instance_id] = self.instances.pop(instance_id)

    def delete_instance(self, instance_id):
        if instance_id not in self.instances:
            raise ValueError(f"Instance {instance_id} not found.")
        del self.instances[instance_id]


def main():
    manager = InstanceManager()

    while True:
        print("\nCloud Instance Manager")
        print("1. Create Instance")
        print("2. Launch Instance")
        print("3. Monitor Instance")
        print("4. Update Instance ID")
        print("5. Delete Instance")
        print("6. Exit")

        choice = input("Enter your choice (1-6): ")

        if choice == '1':
            instance_id = input("Enter new instance ID: ")
            try:
                manager.create_instance(instance_id)
                print(f"Instance {instance_id} created.")
            except ValueError as e:
                print(e)

        elif choice == '2':
            instance_id = input("Enter instance ID to launch: ")
            try:
                manager.launch_instance(instance_id)
                print(f"Instance {instance_id} launched.")
            except ValueError as e:
                print(e)

        elif choice == '3':
            instance_id = input("Enter instance ID to monitor: ")
            try:
                status = manager.monitor_instance(instance_id)
                print(f"Instance {instance_id} status: {status}")
            except ValueError as e:
                print(e)

        elif choice == '4':
            instance_id = input("Enter current instance ID: ")
            new_instance_id = input("Enter new instance ID: ")
            try:
                manager.update_instance(instance_id, new_instance_id)
                print(f"Instance {instance_id} updated to {new_instance_id}.")
            except ValueError as e:
                print(e)

        elif choice == '5':
            instance_id = input("Enter instance ID to delete: ")
            try:
                manager.delete_instance(instance_id)
                print(f"Instance {instance_id} deleted.")
            except ValueError as e:
                print(e)

        elif choice == '6':
            print("Exiting...")
            break

        else:
            print("Invalid choice. Please enter a number between 1 and 6.")

if __name__ == '__main__':
    main()
