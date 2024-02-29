set(CMAKE_AUTOUIC ON)
set(CMAKE_AUTOMOC ON)

find_package(PkgConfig)

pkg_check_modules(LIBNL REQUIRED libnl-3.0)
pkg_check_modules(LIBNL_ROUTE REQUIRED libnl-route-3.0)

set(SOURCES
    main.cpp
    mainwindow.cpp
    mainwindow.ui

    core/Backend.cpp
    core/CanDb.cpp
    core/CanDbMessage.cpp
    core/CanDbNode.cpp
    core/CanDbSignal.cpp
    core/CanMessage.cpp
    core/CanTrace.cpp
    core/ConfigurableWidget.cpp
    core/Log.cpp
    core/LogModel.cpp
    core/MeasurementInterface.cpp
    core/MeasurementNetwork.cpp
    core/MeasurementSetup.cpp

    driver/CanTiming.cpp
    driver/CanInterface.cpp
    driver/CanListener.cpp
    driver/GenericCanSetupPage.cpp
    driver/CanDriver.cpp

    driver/SocketCanDriver/SocketCanDriver.cpp
    driver/SocketCanDriver/SocketCanInterface.cpp
    #driver/PeakCanDriver/PeakCanDriver.cpp
    #driver/PeakCanDriver/PeakCanInterface.cpp
    #driver/CandleApiDriver/CandleApiInterface.cpp
    #driver/CandleApiDriver/CandleApiDriver.cpp
    #driver/CandleApiDriver/CandleApiTiming.cpp

    parser/dbc/DbcParser.cpp
    parser/dbc/DbcTokens.cpp

    window/CanStatusWindow/CanStatusWindow.cpp
    window/CanStatusWindow/CanStatusWindow.h
    window/CanStatusWindow/CanStatusWindow.ui

    window/SetupDialog/SetupDialog.cpp
    window/SetupDialog/SetupDialog.h
    window/SetupDialog/SetupDialog.ui

    window/SetupDialog/SetupDialogTreeItem.cpp
    window/SetupDialog/SetupDialogTreeItem.h
    window/SetupDialog/SetupDialogTreeModel.cpp
    window/SetupDialog/SetupDialogTreeModel.h

    window/SetupDialog/SelectCanInterfacesDialog.cpp
    window/SetupDialog/SelectCanInterfacesDialog.h
    window/SetupDialog/SelectCanInterfacesDialog.ui

    window/TraceWindow/AggregatedTraceViewItem.cpp
    window/TraceWindow/AggregatedTraceViewItem.h
    window/TraceWindow/AggregatedTraceViewModel.cpp
    window/TraceWindow/AggregatedTraceViewModel.h
    window/TraceWindow/BaseTraceViewModel.cpp
    window/TraceWindow/BaseTraceViewModel.h
    window/TraceWindow/LinearTraceViewModel.cpp
    window/TraceWindow/LinearTraceViewModel.h
    window/TraceWindow/TraceViewTypes.h
    window/TraceWindow/TraceWindow.cpp
    window/TraceWindow/TraceWindow.h
    window/TraceWindow/TraceWindow.ui

    window/GraphWindow/GraphWindow.cpp
    window/GraphWindow/GraphWindow.h
    window/GraphWindow/GraphWindow.ui

    window/LogWindow/LogWindow.cpp
    window/LogWindow/LogWindow.h
    window/LogWindow/LogWindow.ui

    cangaroo.qrc
    
)

#qt_wrap_ui(SOURCES mainwindow.ui)
#message(STATUS "${SOURCES}")

add_executable(cangaroo ${SOURCES})
target_link_libraries(cangaroo PRIVATE qt_framework ${LIBNL_LIBRARIES} ${LIBNL_ROUTE_LIBRARIES})
target_include_directories(cangaroo PRIVATE ${CMAKE_CURRENT_SOURCE_DIR} ${LIBNL_INCLUDE_DIRS})
