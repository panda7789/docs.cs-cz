---
title: Změna místa, kam objekt My.Application.Log zapisuje informace
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: bdee0a91360580b156c1734ef4c82139b18ce2b5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336734"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="82223-102">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="82223-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="82223-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span><span class="sxs-lookup"><span data-stu-id="82223-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="82223-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span><span class="sxs-lookup"><span data-stu-id="82223-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="82223-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82223-105">Prerequisites</span></span>

<span data-ttu-id="82223-106">The `Log` object can write information to several log listeners.</span><span class="sxs-lookup"><span data-stu-id="82223-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="82223-107">You need to determine the current configuration of the log listeners before changing the configurations.</span><span class="sxs-lookup"><span data-stu-id="82223-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="82223-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="82223-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

<span data-ttu-id="82223-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="82223-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>

### <a name="to-add-listeners"></a><span data-ttu-id="82223-110">To add listeners</span><span class="sxs-lookup"><span data-stu-id="82223-110">To add listeners</span></span>

1. <span data-ttu-id="82223-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span><span class="sxs-lookup"><span data-stu-id="82223-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="82223-112">\- or -</span><span class="sxs-lookup"><span data-stu-id="82223-112">\- or -</span></span>

     <span data-ttu-id="82223-113">If there is no app.config file:</span><span class="sxs-lookup"><span data-stu-id="82223-113">If there is no app.config file:</span></span>

    1. <span data-ttu-id="82223-114">On the **Project** menu, choose **Add New Item**.</span><span class="sxs-lookup"><span data-stu-id="82223-114">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="82223-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span><span class="sxs-lookup"><span data-stu-id="82223-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>

    3. <span data-ttu-id="82223-116">Click **Add**.</span><span class="sxs-lookup"><span data-stu-id="82223-116">Click **Add**.</span></span>

2. <span data-ttu-id="82223-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span><span class="sxs-lookup"><span data-stu-id="82223-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="82223-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="82223-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="82223-119">Add these elements to that `<listeners>` section.</span><span class="sxs-lookup"><span data-stu-id="82223-119">Add these elements to that `<listeners>` section.</span></span>

    ```xml
    <!-- Uncomment to connect the application file log. -->
    <!-- <add name="FileLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="EventLog" /> -->
    <!-- Uncomment to connect the event log. -->
    <!-- <add name="Delimited" /> -->
    <!-- Uncomment to connect the XML log. -->
    <!-- <add name="XmlWriter" /> -->
    <!-- Uncomment to connect the console log. -->
    <!-- <add name="Console" /> -->
    ```

4. <span data-ttu-id="82223-120">Uncomment the log listeners that you want to receive `Log` messages.</span><span class="sxs-lookup"><span data-stu-id="82223-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>

5. <span data-ttu-id="82223-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="82223-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="82223-122">Add these elements to that `<sharedListeners>` section.</span><span class="sxs-lookup"><span data-stu-id="82223-122">Add these elements to that `<sharedListeners>` section.</span></span>

    ```xml
    <add name="FileLog"
         type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
               Microsoft.VisualBasic, Version=8.0.0.0,
               Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
         initializeData="FileLogWriter" />
    <add name="EventLog"
         type="System.Diagnostics.EventLogTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="sample application"/>
    <add name="Delimited"
         type="System.Diagnostics.DelimitedListTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleDelimitedFile.txt"
         traceOutputOptions="DateTime" />
    <add name="XmlWriter"
         type="System.Diagnostics.XmlWriterTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="c:\temp\sampleLogFile.xml" />
    <add name="Console"
         type="System.Diagnostics.ConsoleTraceListener,
               System, Version=2.0.0.0,
               Culture=neutral, PublicKeyToken=b77a5c561934e089"
         initializeData="true" />
    ```

7. <span data-ttu-id="82223-123">The content of the app.config file should be similar to the following XML:</span><span class="sxs-lookup"><span data-stu-id="82223-123">The content of the app.config file should be similar to the following XML:</span></span>

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
      <system.diagnostics>
        <sources>
          <!-- This section configures My.Application.Log -->
          <source name="DefaultSource" switchName="DefaultSwitch">
            <listeners>
              <add name="FileLog"/>
              <!-- Uncomment to connect the application file log. -->
              <!-- <add name="FileLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="EventLog" /> -->
              <!-- Uncomment to connect the event log. -->
              <!-- <add name="Delimited" /> -->
              <!-- Uncomment to connect the XML log. -->
              <!-- <add name="XmlWriter" /> -->
              <!-- Uncomment to connect the console log. -->
              <!-- <add name="Console" /> -->
            </listeners>
          </source>
        </sources>
        <switches>
          <add name="DefaultSwitch" value="Information" />
        </switches>
        <sharedListeners>
          <add name="FileLog"
               type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
                     Microsoft.VisualBasic, Version=8.0.0.0,
                     Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a"
               initializeData="FileLogWriter" />
          <add name="EventLog"
               type="System.Diagnostics.EventLogTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="sample application"/>
          <add name="Delimited"
               type="System.Diagnostics.DelimitedListTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleDelimitedFile.txt"
               traceOutputOptions="DateTime" />
          <add name="XmlWriter"
               type="System.Diagnostics.XmlWriterTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="c:\temp\sampleLogFile.xml" />
          <add name="Console"
               type="System.Diagnostics.ConsoleTraceListener,
                     System, Version=2.0.0.0,
                     Culture=neutral, PublicKeyToken=b77a5c561934e089"
               initializeData="true" />
        </sharedListeners>
      </system.diagnostics>
    </configuration>
    ```

### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="82223-124">To reconfigure a listener</span><span class="sxs-lookup"><span data-stu-id="82223-124">To reconfigure a listener</span></span>

1. <span data-ttu-id="82223-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span><span class="sxs-lookup"><span data-stu-id="82223-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>

2. <span data-ttu-id="82223-126">The `type` attribute gives the name of the listener type.</span><span class="sxs-lookup"><span data-stu-id="82223-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="82223-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span><span class="sxs-lookup"><span data-stu-id="82223-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="82223-128">Use the strongly named type name to ensure that the right type is used.</span><span class="sxs-lookup"><span data-stu-id="82223-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="82223-129">For more information, see the "To reference a strongly named type" section below.</span><span class="sxs-lookup"><span data-stu-id="82223-129">For more information, see the "To reference a strongly named type" section below.</span></span>

     <span data-ttu-id="82223-130">Some types that you can use are:</span><span class="sxs-lookup"><span data-stu-id="82223-130">Some types that you can use are:</span></span>

    - <span data-ttu-id="82223-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span><span class="sxs-lookup"><span data-stu-id="82223-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>

    - <span data-ttu-id="82223-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span><span class="sxs-lookup"><span data-stu-id="82223-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>

    - <span data-ttu-id="82223-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span><span class="sxs-lookup"><span data-stu-id="82223-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="82223-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span><span class="sxs-lookup"><span data-stu-id="82223-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>

     <span data-ttu-id="82223-135">For information about where other types of log listeners write information, consult that type's documentation.</span><span class="sxs-lookup"><span data-stu-id="82223-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

3. <span data-ttu-id="82223-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span><span class="sxs-lookup"><span data-stu-id="82223-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="82223-137">The meaning of the `initializeData` attribute depends on the trace listener.</span><span class="sxs-lookup"><span data-stu-id="82223-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>

4. <span data-ttu-id="82223-138">After creating the log listener, the application sets the listener's properties.</span><span class="sxs-lookup"><span data-stu-id="82223-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="82223-139">These properties are defined by the other attributes in the `<add>` element.</span><span class="sxs-lookup"><span data-stu-id="82223-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="82223-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span><span class="sxs-lookup"><span data-stu-id="82223-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>

### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="82223-141">To reference a strongly named type</span><span class="sxs-lookup"><span data-stu-id="82223-141">To reference a strongly named type</span></span>

1. <span data-ttu-id="82223-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span><span class="sxs-lookup"><span data-stu-id="82223-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="82223-143">The syntax of a strongly named type is as follows:</span><span class="sxs-lookup"><span data-stu-id="82223-143">The syntax of a strongly named type is as follows:</span></span>

     <span data-ttu-id="82223-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span><span class="sxs-lookup"><span data-stu-id="82223-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>

2. <span data-ttu-id="82223-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span><span class="sxs-lookup"><span data-stu-id="82223-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     <span data-ttu-id="82223-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span><span class="sxs-lookup"><span data-stu-id="82223-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a><span data-ttu-id="82223-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82223-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="82223-148">Postupy: Zápis informací o události do textového souboru</span><span class="sxs-lookup"><span data-stu-id="82223-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="82223-149">Postupy: Zápis do protokolu událostí aplikace</span><span class="sxs-lookup"><span data-stu-id="82223-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
