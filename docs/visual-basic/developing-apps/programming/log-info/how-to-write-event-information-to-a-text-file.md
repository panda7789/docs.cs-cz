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
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="7ea73-102">Postupy: Zápis informací o události do textového souboru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ea73-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="7ea73-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span><span class="sxs-lookup"><span data-stu-id="7ea73-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="7ea73-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span><span class="sxs-lookup"><span data-stu-id="7ea73-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="7ea73-105">To add and configure the file log listener</span><span class="sxs-lookup"><span data-stu-id="7ea73-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="7ea73-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span><span class="sxs-lookup"><span data-stu-id="7ea73-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="7ea73-107">\- or -</span><span class="sxs-lookup"><span data-stu-id="7ea73-107">\- or -</span></span>

     <span data-ttu-id="7ea73-108">If there is no app.config file:</span><span class="sxs-lookup"><span data-stu-id="7ea73-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="7ea73-109">On the **Project** menu, choose **Add New Item**.</span><span class="sxs-lookup"><span data-stu-id="7ea73-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="7ea73-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span><span class="sxs-lookup"><span data-stu-id="7ea73-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="7ea73-111">Click **Add**.</span><span class="sxs-lookup"><span data-stu-id="7ea73-111">Click **Add**.</span></span>

2. <span data-ttu-id="7ea73-112">Locate the `<listeners>` section in the application configuration file.</span><span class="sxs-lookup"><span data-stu-id="7ea73-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="7ea73-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span><span class="sxs-lookup"><span data-stu-id="7ea73-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="7ea73-114">Add this element to that `<listeners>` section:</span><span class="sxs-lookup"><span data-stu-id="7ea73-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="7ea73-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span><span class="sxs-lookup"><span data-stu-id="7ea73-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="7ea73-116">Add this element to that `<sharedListeners>` section:</span><span class="sxs-lookup"><span data-stu-id="7ea73-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="7ea73-117">Change the value of the `customlocation` attribute to the log directory.</span><span class="sxs-lookup"><span data-stu-id="7ea73-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="7ea73-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span><span class="sxs-lookup"><span data-stu-id="7ea73-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="7ea73-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span><span class="sxs-lookup"><span data-stu-id="7ea73-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="7ea73-120">To write event information to the file log</span><span class="sxs-lookup"><span data-stu-id="7ea73-120">To write event information to the file log</span></span>

<span data-ttu-id="7ea73-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span><span class="sxs-lookup"><span data-stu-id="7ea73-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="7ea73-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="7ea73-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>

<span data-ttu-id="7ea73-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span><span class="sxs-lookup"><span data-stu-id="7ea73-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ea73-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ea73-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="7ea73-125">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="7ea73-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="7ea73-126">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="7ea73-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
