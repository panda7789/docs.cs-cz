---
title: 'Postupy: Zápis informací o události do textového souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74352076"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="06de2-102">Postupy: Zápis informací o události do textového souboru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="06de2-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="06de2-103">Objekty `My.Application.Log` a `My.Log` můžete použít k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="06de2-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="06de2-104">Tento příklad ukazuje, `My.Application.Log.WriteEntry` jak pomocí metody protokolovat trasování informací do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="06de2-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="06de2-105">Přidání a konfigurace posluchače protokolu souborů</span><span class="sxs-lookup"><span data-stu-id="06de2-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="06de2-106">Klepněte pravým tlačítkem myši na soubor app.config v **Průzkumníku řešení** a zvolte **Otevřít**.</span><span class="sxs-lookup"><span data-stu-id="06de2-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="06de2-107">\-nebo -</span><span class="sxs-lookup"><span data-stu-id="06de2-107">\- or -</span></span>

     <span data-ttu-id="06de2-108">Pokud není k dispozici žádný soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="06de2-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="06de2-109">V nabídce **Projekt** zvolte **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="06de2-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="06de2-110">V dialogovém okně **Přidat novou položku** zvolte **Konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="06de2-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="06de2-111">Klikněte na **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="06de2-111">Click **Add**.</span></span>

2. <span data-ttu-id="06de2-112">Vyhledejte `<listeners>` oddíl v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="06de2-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="06de2-113">\<Posluchače> části najdete \<v části zdrojové> s atributem název "DefaultSource", který je vnořen v části \<system.diagnostics>, která je vnořena pod oddíl> konfigurace nejvyšší úrovně. \<</span><span class="sxs-lookup"><span data-stu-id="06de2-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="06de2-114">Přidejte tento `<listeners>` prvek do tohoto oddílu:</span><span class="sxs-lookup"><span data-stu-id="06de2-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="06de2-115">Vyhledejte `<sharedListeners>` oddíl `<system.diagnostics>` v části vnořený `<configuration>` pod oddíl nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="06de2-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="06de2-116">Přidejte tento `<sharedListeners>` prvek do tohoto oddílu:</span><span class="sxs-lookup"><span data-stu-id="06de2-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="06de2-117">Změňte hodnotu `customlocation` atributu do adresáře protokolu.</span><span class="sxs-lookup"><span data-stu-id="06de2-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="06de2-118">Chcete-li nastavit hodnotu vlastnosti listener, použijte atribut, který má stejný název jako vlastnost, se všemi písmeny v názvu malá písmena.</span><span class="sxs-lookup"><span data-stu-id="06de2-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="06de2-119">Například `location` atributy `customlocation` a nastavují <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> hodnoty <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> vlastností a.</span><span class="sxs-lookup"><span data-stu-id="06de2-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="06de2-120">Zápis informací o událostech do protokolu souborů</span><span class="sxs-lookup"><span data-stu-id="06de2-120">To write event information to the file log</span></span>

<span data-ttu-id="06de2-121">Pomocí `My.Application.Log.WriteEntry` metody `My.Application.Log.WriteException` or zapište informace do protokolu souborů.</span><span class="sxs-lookup"><span data-stu-id="06de2-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="06de2-122">Další informace naleznete v [tématu How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="06de2-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="06de2-123">Po konfiguraci naslouchací proces protokolu souboru pro sestavení obdrží všechny zprávy, které `My.Application.Log` píše z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="06de2-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="06de2-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="06de2-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="06de2-125">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="06de2-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="06de2-126">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="06de2-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
