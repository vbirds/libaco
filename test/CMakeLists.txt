
macro (aco_register_test test)
    set(name ${test})

    add_executable(test_${name} ${name}.c)
    add_test(test_${name} test_${name})
    add_dependencies(check test_${name})
    add_dependencies(test_${name} libaco::aco)

    aco_target_configure(test_${name} libaco::aco ${ARGN})
endmacro ()

aco_register_test(synopsis)
aco_register_test(tutorial_0)
aco_register_test(tutorial_1)
aco_register_test(tutorial_2)
find_package(Threads QUIET)
if (Threads_FOUND)
    aco_register_test(tutorial_3 Threads::Threads)
endif ()
aco_register_test(tutorial_4)
aco_register_test(tutorial_5)
aco_register_test(tutorial_6)