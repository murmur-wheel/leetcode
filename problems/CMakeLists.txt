# 自动为以 solution 开头的 .cpp 文件创建 target
file(GLOB lc_files RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} "lc*/solution*.cpp")
foreach (lc_file ${lc_files})
    get_filename_component(problem ${lc_file} DIRECTORY)
    get_filename_component(solution ${lc_file} NAME_WLE)
    add_executable("${problem}_${solution}" ${lc_file})
endforeach ()

file(GLOB files RELATIVE ${CMAKE_CURRENT_SOURCE_DIR} "*.cpp")
foreach(file ${files})
    get_filename_component(id ${file} NAME_WLE)
    add_executable("problem-${id}" "${file}")
endforeach ()
