set(CMAKE_INCLUDE_CURRENT_DIR ON)

file(GLOB FOUNDATION_SOURCES ${CMAKE_CURRENT_SOURCE_DIR}/src/*.c
	${CMAKE_CURRENT_SOURCE_DIR}/include/Poco/*.h)

IF(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
   # Mac OS X specific code
   SET(EXTRA "src/SyslogChannel.cpp" "src/SignalHandler.cpp"
   #"src/OpcomChannel.cpp"
   )
ENDIF(${CMAKE_SYSTEM_NAME} MATCHES "Darwin")
IF(${CMAKE_SYSTEM_NAME} MATCHES "Linux")
    # Linux specific code
   SET(EXTRA  "src/SyslogChannel.cpp" "src/SignalHandler.cpp"
   #"src/OpcomChannel.cpp"
   )
ENDIF(${CMAKE_SYSTEM_NAME} MATCHES "Linux")
if(WIN32)
   SET(EXTRA 
     "src/EventLogChannel.cpp"  "src/WindowsConsoleChannel.cpp"
      )

ENDIF()
        message("lib in ${CMAKE_LIBRARY_OUTPUT_DIRECTORY}")        

SET(FOUNDATION_SOURCES ${FOUNDATION_SOURCES}
    src/AbstractObserver.cpp
    src/ActiveDispatcher.cpp
    src/ArchiveStrategy.cpp
    src/Ascii.cpp
    src/ASCIIEncoding.cpp
    src/AsyncChannel.cpp
    src/AtomicCounter.cpp
    src/Base64Decoder.cpp
    src/Base64Encoder.cpp
    src/BinaryReader.cpp
    src/BinaryWriter.cpp
    src/Bugcheck.cpp
#    src/ByteOrder.cpp
    src/Channel.cpp
    src/Checksum.cpp
    src/Condition.cpp
    src/Configurable.cpp
    src/ConsoleChannel.cpp
    src/CountingStream.cpp
    src/DateTime.cpp
    src/DateTimeFormat.cpp
    src/DateTimeFormatter.cpp
    src/DateTimeParser.cpp
    src/Debugger.cpp
    src/DeflatingStream.cpp
    src/DigestEngine.cpp
    src/DigestStream.cpp
    src/DirectoryIterator.cpp
    src/DirectoryWatcher.cpp
    src/DynamicAny.cpp
    src/DynamicAnyHolder.cpp
    src/Environment.cpp
    src/ErrorHandler.cpp
    src/Event.cpp
    src/EventArgs.cpp
    src/Exception.cpp
    src/File.cpp
    src/FileChannel.cpp
    src/FileStream.cpp
    src/FileStreamFactory.cpp
    src/Format.cpp
    src/Formatter.cpp
    src/FormattingChannel.cpp
    src/FPEnvironment.cpp
    src/Glob.cpp
    src/Hash.cpp
    src/HashStatistic.cpp
    src/HexBinaryDecoder.cpp
    src/HexBinaryEncoder.cpp
    src/InflatingStream.cpp
    src/Latin1Encoding.cpp
    src/Latin9Encoding.cpp
    src/LineEndingConverter.cpp
    src/LocalDateTime.cpp
    src/LogFile.cpp
    src/Logger.cpp
    src/LoggingFactory.cpp
    src/LoggingRegistry.cpp
    src/LogStream.cpp
    src/Manifest.cpp
    src/MD4Engine.cpp
    src/MD5Engine.cpp
    src/MemoryPool.cpp
    src/MemoryStream.cpp
    src/Message.cpp
    src/Mutex.cpp
    src/NamedEvent.cpp
    src/NamedMutex.cpp
    src/NestedDiagnosticContext.cpp
    src/Notification.cpp
    src/NotificationCenter.cpp
    src/NotificationQueue.cpp
    src/NullChannel.cpp
    src/NullStream.cpp
    src/NumberFormatter.cpp
    src/NumberParser.cpp
    src/Path.cpp
    src/PatternFormatter.cpp
    src/Pipe.cpp
    src/PipeImpl.cpp
    src/PipeStream.cpp
    src/PriorityNotificationQueue.cpp
    src/Process.cpp
    src/PurgeStrategy.cpp
    src/Random.cpp
    src/RandomStream.cpp
    src/RefCountedObject.cpp
    src/RegularExpression.cpp
    src/RotateStrategy.cpp
    src/Runnable.cpp
    src/RWLock.cpp
    src/Semaphore.cpp
    src/SHA1Engine.cpp
    src/SharedLibrary.cpp
    src/SharedMemory.cpp
    src/SimpleFileChannel.cpp
    src/SplitterChannel.cpp
    src/Stopwatch.cpp
    src/StreamChannel.cpp
    src/StreamConverter.cpp
    src/StreamCopier.cpp
    src/StreamTokenizer.cpp
 #   src/String.cpp
    src/StringTokenizer.cpp
    src/SynchronizedObject.cpp
    src/Task.cpp
    src/TaskManager.cpp
    src/TaskNotification.cpp
    src/TeeStream.cpp
    src/TemporaryFile.cpp
    src/TextBufferIterator.cpp
    src/TextConverter.cpp
    src/TextEncoding.cpp
    src/TextIterator.cpp
    src/Thread.cpp
    src/ThreadLocal.cpp
    src/ThreadPool.cpp
    src/ThreadTarget.cpp
    src/TimedNotificationQueue.cpp
    src/Timer.cpp
    src/Timespan.cpp
    src/Timestamp.cpp
    src/Timezone.cpp
    src/Token.cpp
    src/Unicode.cpp
    src/UnicodeConverter.cpp
    src/URI.cpp
    src/URIStreamFactory.cpp
    src/URIStreamOpener.cpp
    src/UTF8Encoding.cpp
    src/UTF8String.cpp
    src/UTF16Encoding.cpp
    src/UUID.cpp
    src/UUIDGenerator.cpp
    src/Void.cpp
    src/Windows1252Encoding.cpp
)

INCLUDE_DIRECTORIES("include")

ADD_LIBRARY(PocoFoundation STATIC ${FOUNDATION_SOURCES} ${EXTRA})
if(WIN32)
  target_link_libraries(PocoFoundation IPHLPAPI)
endif()
