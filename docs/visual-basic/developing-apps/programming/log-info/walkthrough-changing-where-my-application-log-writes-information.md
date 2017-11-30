---
title: "Změna, kam objekt My.Application.Log zapisuje informace (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c4cd2e675bf1be4f065ee116795a95dae64d13d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="0ef06-102">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ef06-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="0ef06-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0ef06-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="0ef06-104">Tento návod ukazuje, jak přepíší výchozí nastavení, a způsobit, že `Log` objektu k zápisu do jiných součástí naslouchajících protokolům.</span><span class="sxs-lookup"><span data-stu-id="0ef06-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="0ef06-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ef06-105">Prerequisites</span></span>  
 <span data-ttu-id="0ef06-106">`Log` Objekt může zapsat informace do několika naslouchací procesy pro protokoly.</span><span class="sxs-lookup"><span data-stu-id="0ef06-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="0ef06-107">Je nutné určit aktuální konfiguraci naslouchacího procesu protokolu před změnou konfigurace.</span><span class="sxs-lookup"><span data-stu-id="0ef06-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="0ef06-108">Další informace najdete v tématu [návod: určení kam objekt My.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="0ef06-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>  
  
 <span data-ttu-id="0ef06-109">Chcete zkontrolovat [postupy: zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) nebo [postupy: zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="0ef06-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>  
  
### <a name="to-add-listeners"></a><span data-ttu-id="0ef06-110">Chcete-li přidat moduly naslouchání</span><span class="sxs-lookup"><span data-stu-id="0ef06-110">To add listeners</span></span>  
  
1.  <span data-ttu-id="0ef06-111">Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="0ef06-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="0ef06-112">\-nebo –</span><span class="sxs-lookup"><span data-stu-id="0ef06-112">\- or -</span></span>  
  
     <span data-ttu-id="0ef06-113">Pokud není dostupný žádný soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="0ef06-113">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="0ef06-114">Na **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="0ef06-114">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="0ef06-115">Z **přidat novou položku** dialogové okno, vyberte **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="0ef06-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="0ef06-116">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="0ef06-116">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="0ef06-117">Vyhledejte `<listeners>` v oblasti `<source>` část s `name` atribut "DefaultSource", `<sources>` části.</span><span class="sxs-lookup"><span data-stu-id="0ef06-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="0ef06-118">`<sources>` Oddíl je ve `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="0ef06-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="0ef06-119">Přidat tyto prvky, `<listeners>` části.</span><span class="sxs-lookup"><span data-stu-id="0ef06-119">Add these elements to that `<listeners>` section.</span></span>  
  
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
  
4.  <span data-ttu-id="0ef06-120">Zrušením komentáře u naslouchací procesy protokolu, které chcete dostávat `Log` zprávy.</span><span class="sxs-lookup"><span data-stu-id="0ef06-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>  
  
5.  <span data-ttu-id="0ef06-121">Vyhledejte `<sharedListeners>` v části `<system.diagnostics>` oddílem se v nejvyšší úrovně `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="0ef06-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
6.  <span data-ttu-id="0ef06-122">Přidat tyto prvky, `<sharedListeners>` části.</span><span class="sxs-lookup"><span data-stu-id="0ef06-122">Add these elements to that `<sharedListeners>` section.</span></span>  
  
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
  
7.  <span data-ttu-id="0ef06-123">Obsah souboru app.config by měl vypadat přibližně následující kód XML:</span><span class="sxs-lookup"><span data-stu-id="0ef06-123">The content of the app.config file should be similar to the following XML:</span></span>  
  
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
  
### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="0ef06-124">Změna konfigurace naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="0ef06-124">To reconfigure a listener</span></span>  
  
1.  <span data-ttu-id="0ef06-125">Vyhledejte naslouchacího procesu `<add>` element z `<sharedListeners>` oddílu.</span><span class="sxs-lookup"><span data-stu-id="0ef06-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>  
  
2.  <span data-ttu-id="0ef06-126">`type` Atribut poskytuje název typu naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="0ef06-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="0ef06-127">Tento typ musí dědit z <xref:System.Diagnostics.TraceListener> třídy.</span><span class="sxs-lookup"><span data-stu-id="0ef06-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="0ef06-128">Použijte název silně pojmenované typy zajistit, že se používá správný typ.</span><span class="sxs-lookup"><span data-stu-id="0ef06-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="0ef06-129">Další informace najdete v části "tak, aby odkazovaly na silně pojmenované typy".</span><span class="sxs-lookup"><span data-stu-id="0ef06-129">For more information, see the "To reference a strongly named type" section below.</span></span>  
  
     <span data-ttu-id="0ef06-130">Některé typy, které můžete použít jsou:</span><span class="sxs-lookup"><span data-stu-id="0ef06-130">Some types that you can use are:</span></span>  
  
    -   <span data-ttu-id="0ef06-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="0ef06-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>  
  
    -   <span data-ttu-id="0ef06-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje informace do protokolu událostí počítače určeného `initializeData` parametr.</span><span class="sxs-lookup"><span data-stu-id="0ef06-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="0ef06-133"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> a <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> zapisují do zadaného v souboru `initializeData` parametr.</span><span class="sxs-lookup"><span data-stu-id="0ef06-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="0ef06-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> naslouchací proces, který zapisuje do konzoly nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="0ef06-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>  
  
     <span data-ttu-id="0ef06-135">Informace o kde jiné typy naslouchací procesy protokolu zapisují informace najdete v dokumentaci daného typu.</span><span class="sxs-lookup"><span data-stu-id="0ef06-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
3.  <span data-ttu-id="0ef06-136">Aplikace vytvoří objekt protokolu naslouchání, předává `initializeData` atribut jako parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="0ef06-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="0ef06-137">Význam `initializeData` atribut závisí na naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="0ef06-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>  
  
4.  <span data-ttu-id="0ef06-138">Po vytvoření naslouchacího procesu protokolu, aplikace nastaví vlastnosti naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="0ef06-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="0ef06-139">Tyto vlastnosti jsou definované atributy v `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="0ef06-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="0ef06-140">Další informace o vlastnostech pro příslušného naslouchacího procesu naleznete v dokumentaci pro typ této naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="0ef06-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>  
  
### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="0ef06-141">Chcete-li typu silně pojmenované</span><span class="sxs-lookup"><span data-stu-id="0ef06-141">To reference a strongly named type</span></span>  
  
1.  <span data-ttu-id="0ef06-142">Aby se zajistilo, že správné typ se používá pro vaše naslouchací proces protokolu, nezapomeňte použít název plně kvalifikovaný typ a název silně pojmenované sestavení.</span><span class="sxs-lookup"><span data-stu-id="0ef06-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="0ef06-143">Silně pojmenované typy syntaxe vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="0ef06-143">The syntax of a strongly named type is as follows:</span></span>  
  
     <span data-ttu-id="0ef06-144">\<*Název typu*>, \< *název sestavení*>, \< *číslo verze*>, \< *jazykovou verzi*>, \< *silným názvem*></span><span class="sxs-lookup"><span data-stu-id="0ef06-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>  
  
2.  <span data-ttu-id="0ef06-145">Tento příklad kódu ukazuje, jak určit název silně pojmenovaného typu pro plně kvalifikovaný Systen.Diagnostics.FileLogTraceListener"v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="0ef06-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#15](../../../../visual-basic/developing-apps/programming/log-info/codesnippet/VisualBasic/walkthrough-changing-where-my-application-log-writes-information_1.vb)]  
  
     <span data-ttu-id="0ef06-146">Toto je výstup a může sloužit k jednoznačné odkazovat silně pojmenované typy, jako "Chcete-li přidat moduly pro naslouchání" výše uvedený postup.</span><span class="sxs-lookup"><span data-stu-id="0ef06-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>  
  
     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`  
  
## <a name="see-also"></a><span data-ttu-id="0ef06-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ef06-147">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.TraceListener>  
 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>  
 <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>  
 [<span data-ttu-id="0ef06-148">Postupy: zápis informací o události do textového souboru</span><span class="sxs-lookup"><span data-stu-id="0ef06-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)  
 [<span data-ttu-id="0ef06-149">Postupy: zápis do protokolu událostí aplikace</span><span class="sxs-lookup"><span data-stu-id="0ef06-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
