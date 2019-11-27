---
title: 'Postupy: Zápis informací o události do textového souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: c3c81e331eb3d8ee450ba0cac38e57976846ee63
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352076"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="5ec4b-102">Postupy: Zápis informací o události do textového souboru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ec4b-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="5ec4b-103">Pomocí objektů `My.Application.Log` a `My.Log` můžete protokolovat informace o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="5ec4b-104">Tento příklad ukazuje, jak použít metodu `My.Application.Log.WriteEntry` k protokolování informací o trasování do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="5ec4b-105">Přidání a konfigurace naslouchacího procesu protokolu souborů</span><span class="sxs-lookup"><span data-stu-id="5ec4b-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="5ec4b-106">V **Průzkumník řešení** klikněte pravým tlačítkem na soubor App. config a vyberte **otevřít**.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="5ec4b-107">\- nebo-</span><span class="sxs-lookup"><span data-stu-id="5ec4b-107">\- or -</span></span>

     <span data-ttu-id="5ec4b-108">Pokud neexistuje žádný soubor App. config:</span><span class="sxs-lookup"><span data-stu-id="5ec4b-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="5ec4b-109">V nabídce **projekt** klikněte na příkaz **Přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="5ec4b-110">V dialogovém okně **Přidat novou položku** vyberte možnost **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="5ec4b-111">Klikněte na tlačítko **Přidat**.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-111">Click **Add**.</span></span>

2. <span data-ttu-id="5ec4b-112">V konfiguračním souboru aplikace vyhledejte část `<listeners>`.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="5ec4b-113">Část \<Listeners > najdete v oddílu \<zdroj > s názvem "DefaultSource", který je vnořený do oddílu \<System. Diagnostics >, který je vnořený pod oddílem \<konfigurace na nejvyšší úrovni >.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="5ec4b-114">Přidejte tento prvek do tohoto `<listeners>` části:</span><span class="sxs-lookup"><span data-stu-id="5ec4b-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="5ec4b-115">Vyhledejte část `<sharedListeners>` v části `<system.diagnostics>`, která je vnořená do oddílu `<configuration>` nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="5ec4b-116">Přidejte tento prvek do tohoto `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="5ec4b-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="5ec4b-117">Změňte hodnotu atributu `customlocation` na adresář protokolu.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5ec4b-118">Chcete-li nastavit hodnotu vlastnosti naslouchacího procesu, použijte atribut, který má stejný název jako vlastnost, přičemž všechna písmena v názvu jsou malá.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="5ec4b-119">Například atributy `location` a `customlocation` nastavují hodnoty vlastností <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> a <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A>.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="5ec4b-120">Zápis informací o události do protokolu souborů</span><span class="sxs-lookup"><span data-stu-id="5ec4b-120">To write event information to the file log</span></span>

<span data-ttu-id="5ec4b-121">K zápisu informací do protokolu souborů použijte metodu `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException`.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="5ec4b-122">Další informace naleznete v tématu [How to: Write log messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [to: log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="5ec4b-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="5ec4b-123">Po nakonfigurování naslouchacího procesu protokolu souborů pro sestavení obdrží všechny zprávy, které `My.Application.Log` zápisy z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="5ec4b-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ec4b-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ec4b-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="5ec4b-125">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="5ec4b-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="5ec4b-126">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="5ec4b-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
