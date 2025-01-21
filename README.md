class Directory:
    def __init__(self, name):
        self.name = name
        self.subdirectories = []
        self.files = []

    def add_file(self, filename):
        self.files.append(filename)

    def add_subdirectory(self, subdirectory):
        self.subdirectories.append(subdirectory)

    def display(self, level=0):
        print("  " * level + f"[DIR] {self.name}")
        for file in self.files:
            print("  " * (level + 1) + f"- {file}")
        for subdirectory in self.subdirectories:
            subdirectory.display(level + 1)

def create_sample_tree():
    root = Directory("root")
    root.add_file("file1.txt")
    root.add_file("file2.txt")

    subdir1 = Directory("subdir1")
    subdir1.add_file("file3.txt")
    subdir1.add_file("file4.txt")

    subdir2 = Directory("subdir2")
    subdir2.add_file("file5.txt")

    subsubdir1 = Directory("subsubdir1")
    subsubdir1.add_file("file6.txt")

    subdir2.add_subdirectory(subsubdir1)
    root.add_subdirectory(subdir1)
    root.add_subdirectory(subdir2)

    return root

if __name__ == "__main__":
    tree = create_sample_tree()
    tree.display()
