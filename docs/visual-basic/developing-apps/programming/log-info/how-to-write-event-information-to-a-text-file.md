---
title: "Postupy: Zápis informací o události do textového souboru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 944d874de5c3872f9efe5e287e5354c94c792b95
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="f4d7d-102">Postupy: Zápis informací o události do textového souboru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4d7d-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="f4d7d-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="f4d7d-104">Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metoda do protokolu informace trasování do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="f4d7d-105">K přidání a konfiguraci naslouchacího procesu souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="f4d7d-105">To add and configure the file log listener</span></span>  
  
1.  <span data-ttu-id="f4d7d-106">Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="f4d7d-107">\-nebo –</span><span class="sxs-lookup"><span data-stu-id="f4d7d-107">\- or -</span></span>  
  
     <span data-ttu-id="f4d7d-108">Pokud není dostupný žádný soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="f4d7d-108">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="f4d7d-109">Na **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="f4d7d-110">Z **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="f4d7d-111">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-111">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="f4d7d-112">Vyhledejte `<listeners>` oddílu v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="f4d7d-113">Zjistíte, \<naslouchací procesy > tématu \<zdroje > části s názvem atributu "DefaultSource", která je vnořená \<system.diagnostics > oddíl, což je vnořená pod nejvyšší úrovně \<konfigurace > části.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3.  <span data-ttu-id="f4d7d-114">Přidejte tento element do `<listeners>` části:</span><span class="sxs-lookup"><span data-stu-id="f4d7d-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  <span data-ttu-id="f4d7d-115">Vyhledejte `<sharedListeners>` tématu `<system.diagnostics>` část, v nejvyšší úrovni `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="f4d7d-116">Přidejte tento element do `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="f4d7d-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="f4d7d-117">Změňte hodnotu `customlocation` atribut adresář protokolu.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f4d7d-118">Pokud chcete nastavit hodnotu vlastnosti naslouchací proces, použijte atribut, který má stejný název jako vlastnost, kde jsou všechna písmena na malá písmena název.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="f4d7d-119">Například `location` a `customlocation` atributy nastavte hodnoty <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> a <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="f4d7d-120">Zápis informací o události do souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="f4d7d-120">To write event information to the file log</span></span>  
  
-   <span data-ttu-id="f4d7d-121">Použití `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` metoda při zápisu informací do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="f4d7d-122">Další informace najdete v tématu [postupy: zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) a [postup: výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f4d7d-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="f4d7d-123">Po dokončení konfigurace naslouchací proces protokolu souboru pro sestavení, obdrží všechny zprávy, která `My.Application.Log` zapíše z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="f4d7d-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4d7d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4d7d-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="f4d7d-125">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="f4d7d-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="f4d7d-126">Postupy: protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="f4d7d-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
