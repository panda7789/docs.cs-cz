---
title: 'Postupy: Zápis informací o události do textového souboru (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 3adb594ee42b7b1fad77a54af04bb9f37f30c19a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589055"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="f15e1-102">Postupy: Zápis informací o události do textového souboru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15e1-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>
<span data-ttu-id="f15e1-103">Můžete použít `My.Application.Log` a `My.Log` objekty k protokolování informací o událostech, ke kterým dochází ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f15e1-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="f15e1-104">Tento příklad ukazuje způsob použití `My.Application.Log.WriteEntry` metoda do protokolu informace trasování do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="f15e1-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>  
  
### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="f15e1-105">K přidání a konfiguraci naslouchacího procesu souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="f15e1-105">To add and configure the file log listener</span></span>  
  
1.  <span data-ttu-id="f15e1-106">Klikněte pravým tlačítkem na app.config v **Průzkumníku řešení** a zvolte **otevřete**.</span><span class="sxs-lookup"><span data-stu-id="f15e1-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="f15e1-107">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="f15e1-107">\- or -</span></span>  
  
     <span data-ttu-id="f15e1-108">Pokud není dostupný žádný soubor app.config:</span><span class="sxs-lookup"><span data-stu-id="f15e1-108">If there is no app.config file:</span></span>  
  
    1.  <span data-ttu-id="f15e1-109">Na **projektu** nabídce zvolte **přidat novou položku**.</span><span class="sxs-lookup"><span data-stu-id="f15e1-109">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="f15e1-110">Z **přidat novou položku** dialogovém okně vyberte **konfigurační soubor aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f15e1-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="f15e1-111">Klikněte na tlačítko **přidat**.</span><span class="sxs-lookup"><span data-stu-id="f15e1-111">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="f15e1-112">Vyhledejte `<listeners>` oddílu v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f15e1-112">Locate the `<listeners>` section in the application configuration file.</span></span>  
  
     <span data-ttu-id="f15e1-113">Zjistíte, \<naslouchací procesy > tématu \<zdroje > části s názvem atributu "DefaultSource", která je vnořená \<system.diagnostics > oddíl, což je vnořená pod nejvyšší úrovně \<konfigurace > části.</span><span class="sxs-lookup"><span data-stu-id="f15e1-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>  
  
3.  <span data-ttu-id="f15e1-114">Přidejte tento element do `<listeners>` části:</span><span class="sxs-lookup"><span data-stu-id="f15e1-114">Add this element to that `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener" />  
    ```  
  
4.  <span data-ttu-id="f15e1-115">Vyhledejte `<sharedListeners>` tématu `<system.diagnostics>` část, v nejvyšší úrovni `<configuration>` části.</span><span class="sxs-lookup"><span data-stu-id="f15e1-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="f15e1-116">Přidejte tento element do `<sharedListeners>` části:</span><span class="sxs-lookup"><span data-stu-id="f15e1-116">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="FileLogListener"   
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,   
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,   
              PublicKeyToken=b03f5f7f11d50a3a"  
        initializeData="FileLogListenerWriter"  
        location="Custom"  
        customlocation="c:\temp\" />  
    ```  
  
     <span data-ttu-id="f15e1-117">Změňte hodnotu `customlocation` atribut adresář protokolu.</span><span class="sxs-lookup"><span data-stu-id="f15e1-117">Change the value of the `customlocation` attribute to the log directory.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f15e1-118">Pokud chcete nastavit hodnotu vlastnosti naslouchací proces, použijte atribut, který má stejný název jako vlastnost, kde jsou všechna písmena na malá písmena název.</span><span class="sxs-lookup"><span data-stu-id="f15e1-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="f15e1-119">Například `location` a `customlocation` atributy nastavte hodnoty <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> a <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f15e1-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>  
  
### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="f15e1-120">Zápis informací o události do souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="f15e1-120">To write event information to the file log</span></span>  
  
-   <span data-ttu-id="f15e1-121">Použití `My.Application.Log.WriteEntry` nebo `My.Application.Log.WriteException` metoda při zápisu informací do souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="f15e1-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="f15e1-122">Další informace najdete v tématu [postupy: zápis zpráv protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) a [postup: výjimky protokolu](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span><span class="sxs-lookup"><span data-stu-id="f15e1-122">For more information, see [How to: Write Log Messages](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md) and [How to: Log Exceptions](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md).</span></span>  
  
     <span data-ttu-id="f15e1-123">Po dokončení konfigurace naslouchací proces protokolu souboru pro sestavení, obdrží všechny zprávy, která `My.Application.Log` zapíše z tohoto sestavení.</span><span class="sxs-lookup"><span data-stu-id="f15e1-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15e1-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="f15e1-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>  
 <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>  
 [<span data-ttu-id="f15e1-125">Práce s protokoly aplikací</span><span class="sxs-lookup"><span data-stu-id="f15e1-125">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="f15e1-126">Postupy: Protokolování výjimek</span><span class="sxs-lookup"><span data-stu-id="f15e1-126">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
