---
title: "Postupy: Dědění formulářů Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b91cde9e04ab37f0dca7b1e36be8608310ac35db
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="13948-102">Postupy: Dědění formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="13948-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="13948-103">Vytvoření nové Windows Forms pomocí dědění z podkladové formuláře je užitečný způsob, jak duplicitní maximální úsilí bez průchodu přes proces pokaždé, když to vyžadují zcela nové vytvoření formuláře.</span><span class="sxs-lookup"><span data-stu-id="13948-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="13948-104">Další informace o dědění formulářů pomocí čas návrhu **výběr dědičnosti** dialogové okno a postup vizuálně rozlišit mezi úrovněmi zabezpečení zděděná ovládací prvky najdete v tématu [postupy: dědění formulářů pomocí Dialogové okno Výběr dědičnosti](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="13948-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="13948-105">**Poznámka:** aby bylo možné zdědit z formuláře, soubor nebo obor názvů obsahující tato forma musí mít sestavily do spustitelného souboru nebo knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="13948-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="13948-106">Pro sestavení projektu, zvolte **sestavení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="13948-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="13948-107">Odkaz na obor názvů navíc musí přidat k třídě dědí formuláře.</span><span class="sxs-lookup"><span data-stu-id="13948-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="13948-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="13948-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="13948-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="13948-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="13948-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="13948-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="13948-111">Chcete-li zdědit formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="13948-111">To inherit a form programmatically</span></span>  
  
1.  <span data-ttu-id="13948-112">Ve třídě přidejte odkaz na obor názvů obsahující formulář, který chcete dědí.</span><span class="sxs-lookup"><span data-stu-id="13948-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2.  <span data-ttu-id="13948-113">V definici třídy přidejte odkaz na formulář dědění z.</span><span class="sxs-lookup"><span data-stu-id="13948-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="13948-114">Obor názvů, který obsahuje formulář, následuje dobou, pak název základní formuláři samotnému by měla obsahovat odkaz na.</span><span class="sxs-lookup"><span data-stu-id="13948-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="13948-115">Při dědění formulářů, mějte na paměti, která mohou se vyskytnout potíže se s ohledem na obslužné rutiny událostí se volala dvakrát, protože každé události je zpracovanou základní třídy a zděděné třídy.</span><span class="sxs-lookup"><span data-stu-id="13948-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="13948-116">Další informace o tom, jak zamezit tomuto problému najdete v tématu [řešení potíží s zděděná obslužné rutiny událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="13948-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13948-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="13948-117">See Also</span></span>  
 [<span data-ttu-id="13948-118">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="13948-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="13948-119">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="13948-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="13948-120">using</span><span class="sxs-lookup"><span data-stu-id="13948-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)  
 [<span data-ttu-id="13948-121">Účinky úpravy vzhledu základního formuláře</span><span class="sxs-lookup"><span data-stu-id="13948-121">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [<span data-ttu-id="13948-122">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="13948-122">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
