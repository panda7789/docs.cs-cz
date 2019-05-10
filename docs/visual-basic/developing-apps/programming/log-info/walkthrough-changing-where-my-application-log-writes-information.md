---
title: Změna, kam objekt My.Application.Log zapisuje informace (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: cba90119fa6f26946e72ce097074f275178ff33b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593342"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="0933a-102">Návod: Změna, kam objekt My.Application.Log zapisuje informace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0933a-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="0933a-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o události, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0933a-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="0933a-104">Tento návod ukazuje, jak přepsat výchozí nastavení a způsobit, `Log` objekt k zápisu do jiných naslouchacích procesů protokolu.</span><span class="sxs-lookup"><span data-stu-id="0933a-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0933a-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0933a-105">Prerequisites</span></span>  
 <span data-ttu-id="0933a-106">`Log` Objektu lze zapsat informace na několik součástí naslouchajících protokolům.</span><span class="sxs-lookup"><span data-stu-id="0933a-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="0933a-107">Je nutné určit aktuální konfiguraci součásti naslouchající protokolům před změnou konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0933a-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="0933a-108">Další informace najdete v tématu [názorný postup: Určení, kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="0933a-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="0933a-109">Můžete chtít zkontrolovat [jak: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) nebo [jak: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="0933a-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="0933a-110">Chcete-li přidat naslouchací procesy</span><span class="sxs-lookup"><span data-stu-id="0933a-110">To add listeners</span></span>  
  
1. <span data-ttu-id="0933a-111">Klikněte pravým tlačítkem na app.config **Průzkumníka řešení** a zvolte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="0933a-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="0933a-112">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="0933a-112">\- or -</span></span>  
  
     <span data-ttu-id="0933a-113">Pokud není dostupný žádný soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="0933a-113">If there is no app.config file:</span></span>  
  
    1. <span data-ttu-id="0933a-114">Na **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="0933a-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2. <span data-ttu-id="0933a-115">Z **přidat novou položku** dialogu **konfiguračního souboru aplikace**.</span><span class="sxs-lookup"><span data-stu-id="0933a-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3. <span data-ttu-id="0933a-116">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="0933a-116">Click **Add**.</span></span>  
  
2. <span data-ttu-id="0933a-117">Vyhledejte `<listeners>` pod `<source>` části s `name` atribut "DefaultSource" `<sources>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0933a-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="0933a-118">`<sources>` Oddíl je ve `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0933a-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3. <span data-ttu-id="0933a-119">Přidejte tyto prvky do `<listeners>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0933a-119">Add these elements to that `<listeners>` section.</span></span>  
  
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
  
4. <span data-ttu-id="0933a-120">Zrušením komentáře u součásti naslouchající protokolům, které chcete dostávat `Log` zprávy.</span><span class="sxs-lookup"><span data-stu-id="0933a-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5. <span data-ttu-id="0933a-121">Vyhledejte `<sharedListeners>` sekci `<system.diagnostics>` části na nejvyšší úrovni `<configuration>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0933a-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6. <span data-ttu-id="0933a-122">Přidejte tyto prvky do `<sharedListeners>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0933a-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
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
  
7. <span data-ttu-id="0933a-123">Obsah souboru app.config by měl být podobně jako následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="0933a-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="0933a-124">Chcete-li překonfigurovat naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="0933a-124">To reconfigure a listener</span></span>  
  
1. <span data-ttu-id="0933a-125">Vyhledejte naslouchacího procesu `<add>` element z `<sharedListeners>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0933a-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2. <span data-ttu-id="0933a-126">`type` Atribut poskytuje název typu naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="0933a-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="0933a-127">Tento typ musí dědit z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="0933a-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="0933a-128">Chcete-li zajistit, aby používal správný typ použijte název silným názvem typu.</span><span class="sxs-lookup"><span data-stu-id="0933a-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="0933a-129">Další informace najdete v části "k odkazování silným názvem typu".</span><span class="sxs-lookup"><span data-stu-id="0933a-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="0933a-130">Jsou některé typy, které můžete použít:</span><span class="sxs-lookup"><span data-stu-id="0933a-130">Some types that you can use are:</span></span>  
  
    - <span data-ttu-id="0933a-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="0933a-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    - <span data-ttu-id="0933a-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje informace do protokolu událostí počítače určené `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="0933a-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    - <span data-ttu-id="0933a-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> naslouchacích procesů, které zapisovat do souboru zadaného v `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="0933a-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    - <span data-ttu-id="0933a-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje do konzoly příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0933a-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="0933a-135">Informace o tom, kde psát jiných typů součástí naslouchajících protokolům informace najdete v dokumentaci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="0933a-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3. <span data-ttu-id="0933a-136">Když se aplikace vytvoří objekt protokolu naslouchací proces, předá `initializeData` atribut jako parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0933a-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="0933a-137">Význam `initializeData` atributu závisí na naslouchací služby stopy.</span><span class="sxs-lookup"><span data-stu-id="0933a-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4. <span data-ttu-id="0933a-138">Po vytvoření naslouchacího procesu protokolu aplikace nastaví vlastnosti naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="0933a-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="0933a-139">Tyto vlastnosti jsou definovány další atributy `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0933a-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="0933a-140">Další informace o vlastnostech pro příslušného naslouchacího procesu naleznete v dokumentaci pro typ tohoto naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="0933a-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="0933a-141">Chcete-li odkazovat na typ silným názvem</span><span class="sxs-lookup"><span data-stu-id="0933a-141">To reference a strongly named type</span></span>  
  
1. <span data-ttu-id="0933a-142">Chcete-li zajistit, aby používal správný typ pro vaše naslouchací proces protokolu, nezapomeňte použít plně kvalifikovaného názvu a názvu sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="0933a-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="0933a-143">Syntaxe typu silným názvem je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0933a-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="0933a-144">\<*Název typu*>, \< *název sestavení*>, \< *číslo verze*>, \< *jazykovou verzi*>, \< *silným názvem*></span><span class="sxs-lookup"><span data-stu-id="0933a-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2. <span data-ttu-id="0933a-145">Tento příklad kódu ukazuje, jak určit název silně pojmenované typy pro plně kvalifikovaný Systen.Diagnostics.FileLogTraceListener"v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="0933a-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]  
  
     <span data-ttu-id="0933a-146">Toto je výstup, a to je možné jednoznačně odkazovat na typ silným názvem, stejně jako v "pro přidání posluchače" výše uvedeného postupu.</span><span class="sxs-lookup"><span data-stu-id="0933a-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="0933a-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0933a-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="0933a-148">Postupy: Zápis informací o události do textového souboru</span><span class="sxs-lookup"><span data-stu-id="0933a-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="0933a-149">Postupy: Zápis do protokolu událostí aplikace</span><span class="sxs-lookup"><span data-stu-id="0933a-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
