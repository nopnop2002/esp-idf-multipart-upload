set(COMPONENT_SRCS main.c multipart-upload.c)
set(COMPONENT_ADD_INCLUDEDIRS ".")

register_component()
spiffs_create_partition_image(storage ../images FLASH_IN_PROJECT)
