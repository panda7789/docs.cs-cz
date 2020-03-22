---
title: Změna místa, kam objekt My.Application.Log zapisuje informace
ms.date: 07/20/2015
helpviewer_keywords:
- My.Application.Log object, walkthroughs
- event logs, changing output location
ms.assetid: ecc74f95-743c-450d-93f6-09a30db0fe4a
ms.openlocfilehash: bdee0a91360580b156c1734ef4c82139b18ce2b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74336734"
---
# <a name="walkthrough-changing-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="b5739-102">Návod: Změna místa, kam objekt My.Application.Log zapisuje informace (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5739-102">Walkthrough: Changing Where My.Application.Log Writes Information (Visual Basic)</span></span>

<span data-ttu-id="b5739-103">Objekty `My.Application.Log` a `My.Log` můžete použít k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b5739-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="b5739-104">Tento návod ukazuje, jak přepsat výchozí nastavení `Log` a způsobit, že objekt zapisovat do jiných posluchačů protokolu.</span><span class="sxs-lookup"><span data-stu-id="b5739-104">This walkthrough shows how to override the default settings and cause the `Log` object to write to other log listeners.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5739-105">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b5739-105">Prerequisites</span></span>

<span data-ttu-id="b5739-106">Objekt `Log` může zapisovat informace do několika naslouchacích procesů protokolu.</span><span class="sxs-lookup"><span data-stu-id="b5739-106">The `Log` object can write information to several log listeners.</span></span> <span data-ttu-id="b5739-107">Před změnou konfigurací je třeba určit aktuální konfiguraci posluchačů protokolu.</span><span class="sxs-lookup"><span data-stu-id="b5739-107">You need to determine the current configuration of the log listeners before changing the configurations.</span></span> <span data-ttu-id="b5739-108">Další informace naleznete [v tématu Návod: Určení, kde my.Application.Log zapisuje informace](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span><span class="sxs-lookup"><span data-stu-id="b5739-108">For more information, see [Walkthrough: Determining Where My.Application.Log Writes Information](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-determining-where-my-application-log-writes-information.md).</span></span>

<span data-ttu-id="b5739-109">Můžete si přečíst [postup: Zápis informací o události do textového souboru](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) nebo [Jak: Zápis do protokolu událostí aplikace](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span><span class="sxs-lookup"><span data-stu-id="b5739-109">You may want to review [How to: Write Event Information to a Text File](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md) or [How to: Write to an Application Event Log](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md).</span></span>

### <a name="to-add-listeners"></a><span data-ttu-id="b5739-110">Přidání posluchačů</span><span class="sxs-lookup"><span data-stu-id="b5739-110">To add listeners</span></span>

1. <span data-ttu-id="b5739-111">Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.</span><span class="sxs-lookup"><span data-stu-id="b5739-111">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="b5739-112">\-nebo -</span><span class="sxs-lookup"><span data-stu-id="b5739-112">\- or -</span></span>

     <span data-ttu-id="b5739-113">Pokud není k dispozici žádný soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="b5739-113">If there is no app.config file:</span></span>

    1. <span data-ttu-id="b5739-114">V nabídce **Projekt** zvolte **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="b5739-114">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="b5739-115">V dialogovém okně **Přidat novou položku** vyberte **Konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="b5739-115">From the **Add New Item** dialog box, select **Application Configuration File**.</span></span>

    3. <span data-ttu-id="b5739-116">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="b5739-116">Click **Add**.</span></span>

2. <span data-ttu-id="b5739-117">Vyhledejte `<listeners>` oddíl pod `<source>` oddílem `name` s atributem "DefaultSource" v `<sources>` části.</span><span class="sxs-lookup"><span data-stu-id="b5739-117">Locate the `<listeners>` section, under the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section.</span></span> <span data-ttu-id="b5739-118">Sekce `<sources>` je v `<system.diagnostics>` sekci, v horní `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="b5739-118">The `<sources>` section is in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

3. <span data-ttu-id="b5739-119">Přidejte tyto `<listeners>` prvky do tohoto oddílu.</span><span class="sxs-lookup"><span data-stu-id="b5739-119">Add these elements to that `<listeners>` section.</span></span>

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

4. <span data-ttu-id="b5739-120">Odkomentujte posluchače protokolu, `Log` které chcete přijímat zprávy.</span><span class="sxs-lookup"><span data-stu-id="b5739-120">Uncomment the log listeners that you want to receive `Log` messages.</span></span>

5. <span data-ttu-id="b5739-121">Vyhledejte `<sharedListeners>` oddíl v `<system.diagnostics>` části v části `<configuration>` nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="b5739-121">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>

6. <span data-ttu-id="b5739-122">Přidejte tyto `<sharedListeners>` prvky do tohoto oddílu.</span><span class="sxs-lookup"><span data-stu-id="b5739-122">Add these elements to that `<sharedListeners>` section.</span></span>

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

7. <span data-ttu-id="b5739-123">Obsah souboru app.config by měl být podobný následujícímu xml:</span><span class="sxs-lookup"><span data-stu-id="b5739-123">The content of the app.config file should be similar to the following XML:</span></span>

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

### <a name="to-reconfigure-a-listener"></a><span data-ttu-id="b5739-124">Změna konfigurace naslouchací proces</span><span class="sxs-lookup"><span data-stu-id="b5739-124">To reconfigure a listener</span></span>

1. <span data-ttu-id="b5739-125">Vyhledejte `<add>` prvek posluchače `<sharedListeners>` z oddílu.</span><span class="sxs-lookup"><span data-stu-id="b5739-125">Locate the listener's `<add>` element from the `<sharedListeners>` section.</span></span>

2. <span data-ttu-id="b5739-126">Atribut `type` udává název typu naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="b5739-126">The `type` attribute gives the name of the listener type.</span></span> <span data-ttu-id="b5739-127">Tento typ musí <xref:System.Diagnostics.TraceListener> dědit z třídy.</span><span class="sxs-lookup"><span data-stu-id="b5739-127">This type must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="b5739-128">Pomocí silně pojmenovaného názvu typu zajistěte, aby byl použit správný typ.</span><span class="sxs-lookup"><span data-stu-id="b5739-128">Use the strongly named type name to ensure that the right type is used.</span></span> <span data-ttu-id="b5739-129">Další informace naleznete v části "Chcete-li odkazovat na silně pojmenovaný typ" níže.</span><span class="sxs-lookup"><span data-stu-id="b5739-129">For more information, see the "To reference a strongly named type" section below.</span></span>

     <span data-ttu-id="b5739-130">Některé typy, které můžete použít, jsou:</span><span class="sxs-lookup"><span data-stu-id="b5739-130">Some types that you can use are:</span></span>

    - <span data-ttu-id="b5739-131">Naslouchací <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> proces, který zapisuje do protokolu souborů.</span><span class="sxs-lookup"><span data-stu-id="b5739-131">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener, which writes to a file log.</span></span>

    - <span data-ttu-id="b5739-132">Naslouchací <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> proces, který zapisuje informace do protokolu událostí počítače určeného parametrem. `initializeData`</span><span class="sxs-lookup"><span data-stu-id="b5739-132">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener, which writes information to the computer event log specified by the `initializeData` parameter.</span></span>

    - <span data-ttu-id="b5739-133">A <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> naslouchací procesy, `initializeData` které zapisují do souboru určeného v parametru.</span><span class="sxs-lookup"><span data-stu-id="b5739-133">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners, which write to the file specified in the `initializeData` parameter.</span></span>

    - <span data-ttu-id="b5739-134">Naslouchací <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> proces, který zapisuje do konzoly příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="b5739-134">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener, which writes to the command-line console.</span></span>

     <span data-ttu-id="b5739-135">Informace o tom, kde jiné typy posluchačů protokolu psát informace, naleznete v dokumentaci tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="b5739-135">For information about where other types of log listeners write information, consult that type's documentation.</span></span>

3. <span data-ttu-id="b5739-136">Když aplikace vytvoří objekt posluchače protokolu, `initializeData` předá atribut jako parametr konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="b5739-136">When the application creates the log-listener object, it passes the `initializeData` attribute as the constructor parameter.</span></span> <span data-ttu-id="b5739-137">Význam atributu `initializeData` závisí na naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="b5739-137">The meaning of the `initializeData` attribute depends on the trace listener.</span></span>

4. <span data-ttu-id="b5739-138">Po vytvoření naslouchací proces protokolu aplikace nastaví vlastnosti posluchače.</span><span class="sxs-lookup"><span data-stu-id="b5739-138">After creating the log listener, the application sets the listener's properties.</span></span> <span data-ttu-id="b5739-139">Tyto vlastnosti jsou definovány ostatními atributy v elementu. `<add>`</span><span class="sxs-lookup"><span data-stu-id="b5739-139">These properties are defined by the other attributes in the `<add>` element.</span></span> <span data-ttu-id="b5739-140">Další informace o vlastnostech pro konkrétní naslouchací proces naleznete v dokumentaci k typu tohoto naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="b5739-140">For more information on the properties for a particular listener, see the documentation for that listener's type.</span></span>

### <a name="to-reference-a-strongly-named-type"></a><span data-ttu-id="b5739-141">Odkaz na silně pojmenovaný typ</span><span class="sxs-lookup"><span data-stu-id="b5739-141">To reference a strongly named type</span></span>

1. <span data-ttu-id="b5739-142">Chcete-li zajistit, že správný typ se používá pro posluchače protokolu, ujistěte se, že používáte plně kvalifikovaný název typu a silně pojmenovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="b5739-142">To ensure that the right type is used for your log listener, make sure to use the fully qualified type name and the strongly named assembly name.</span></span> <span data-ttu-id="b5739-143">Syntaxe silně pojmenovaného typu je následující:</span><span class="sxs-lookup"><span data-stu-id="b5739-143">The syntax of a strongly named type is as follows:</span></span>

     <span data-ttu-id="b5739-144">\<*název>,* \< *název* sestavení \<>, \<číslo *verze*>,> jazykové *verze,* \< *silný název*></span><span class="sxs-lookup"><span data-stu-id="b5739-144">\<*type name*>, \<*assembly name*>, \<*version number*>, \<*culture*>, \<*strong name*></span></span>

2. <span data-ttu-id="b5739-145">Tento příklad kódu ukazuje, jak určit silně pojmenovaný název typu pro plně kvalifikovaný typ – "System.Diagnostics.FileLogTraceListener" v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="b5739-145">This code example shows how to determine the strongly named type name for a fully qualified type—"System.Diagnostics.FileLogTraceListener" in this case.</span></span>

     [!code-vb[VbVbalrMyApplicationLog#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#15)]

     <span data-ttu-id="b5739-146">Toto je výstup a lze jej použít k jedinečným odkazem na silně pojmenovaný typ, jako v postupu "Chcete-li přidat posluchače" výše.</span><span class="sxs-lookup"><span data-stu-id="b5739-146">This is the output, and it can be used to uniquely reference a strongly named type, as in the "To add listeners" procedure above.</span></span>

     `Microsoft.VisualBasic.Logging.FileLogTraceListener, Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a`

## <a name="see-also"></a><span data-ttu-id="b5739-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5739-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceListener>
- <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType>
- <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>
- [<span data-ttu-id="b5739-148">Postupy: Zápis informací o události do textového souboru</span><span class="sxs-lookup"><span data-stu-id="b5739-148">How to: Write Event Information to a Text File</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-event-information-to-a-text-file.md)
- [<span data-ttu-id="b5739-149">Postupy: Zápis do protokolu událostí aplikace</span><span class="sxs-lookup"><span data-stu-id="b5739-149">How to: Write to an Application Event Log</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-to-an-application-event-log.md)
