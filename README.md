# Hey! I'm Filing Here

In this lab I implemented an `ext2-create` program that writes a valid 1 MiB
ext2 filesystem image (`cs111-base.img`) with 1 KiB blocks and space for 128
inodes. The image contains two directories (`/` and `lost+found`), one regular
file (`hello-world`), and one symbolic link (`hello -> hello-world`).

The following functions were completed in `ext2-create.c`:

- `write_superblock`
- `write_block_group_descriptor_table`
- `write_block_bitmap`
- `write_inode_bitmap`
- `write_inode_table`
- `write_root_dir_block`
- `write_hello_world_file_block`

## Building

Run `make` to compile the `ext2-create` executable:

```sh
make
```

## Running

Run the executable to create the filesystem image `cs111-base.img` in the
current directory:

```sh
./ext2-create
```

You can then inspect and verify the image:

```sh
dumpe2fs cs111-base.img        # dump filesystem information
fsck.ext2 -f cs111-base.img    # check the filesystem for errors
```

To mount it and look at the contents:

```sh
mkdir mnt
sudo mount -o loop cs111-base.img mnt
ls -ain mnt/
sudo umount mnt
rmdir mnt
```

The provided tests can be run with:

```sh
python -m unittest
```

## Cleaning up

Run `make clean` to remove the build artifacts and the generated image:

```sh
make clean
```
