---
title: 'Postupy: Dědění formulářů Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: 275ae52a36ed9766e2569bd6c8ecdea78ea56e0b
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44709396"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="2745a-102">Postupy: Dědění formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="2745a-102">How to: Inherit Windows Forms</span></span>
<span data-ttu-id="2745a-103">Vytvoření nového formuláře Windows děděním z podkladové formuláře je šikovný způsob, jak duplikovat vynaloží veškeré úsilí bez nutnosti kontaktovat proces pokaždé, když chcete, aby zcela opětovné vytvoření formuláře.</span><span class="sxs-lookup"><span data-stu-id="2745a-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>  
  
 <span data-ttu-id="2745a-104">Další informace o dědění formulářů pomocí času návrhu **výběr dědičnosti** dialogové okno a tom, jak vizuálně rozlišovat mezi úrovněmi zabezpečení zděděné ovládacích prvků naleznete v tématu [postupy: dědění formulářů pomocí Dialogové okno Výběr dědičnosti](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span><span class="sxs-lookup"><span data-stu-id="2745a-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](../../../../docs/framework/winforms/advanced/how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>  
  
 <span data-ttu-id="2745a-105">**Poznámka:** aby bylo možné zdědit z formuláře, soubor nebo obor názvů obsahující, které tvoří musí sestavené do spustitelného souboru nebo knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="2745a-105">**Note** In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="2745a-106">Sestavte projekt, zvolte **sestavení** z **sestavení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="2745a-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="2745a-107">Odkaz na obor názvů navíc musí přidat na třídu, která dědí formuláře.</span><span class="sxs-lookup"><span data-stu-id="2745a-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span> <span data-ttu-id="2745a-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="2745a-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2745a-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="2745a-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2745a-110">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2745a-110">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-inherit-a-form-programmatically"></a><span data-ttu-id="2745a-111">Dědění formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="2745a-111">To inherit a form programmatically</span></span>  
  
1.  <span data-ttu-id="2745a-112">Ve své třídě přidejte odkaz na obor názvů obsahující formulář, do kterého chcete dědí.</span><span class="sxs-lookup"><span data-stu-id="2745a-112">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>  
  
2.  <span data-ttu-id="2745a-113">V definici třídy přidejte odkaz na formulář dědí.</span><span class="sxs-lookup"><span data-stu-id="2745a-113">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="2745a-114">Odkaz na by měly zahrnovat obor názvů obsahující formulář, následovaných tečkou, pak název základní samotný formulář.</span><span class="sxs-lookup"><span data-stu-id="2745a-114">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>  
  
    ```vb  
    Public Class Form2  
        Inherits Namespace1.Form1  
    ```  
  
    ```csharp  
    public class Form2 : Namespace1.Form1  
    ```  
  
 <span data-ttu-id="2745a-115">Při dědění formulářů, mějte na paměti, mohou se vyskytnout problémy z hlediska obslužné rutiny událostí volána dvakrát, protože se zpracovává každé události základní třídy a zděděná třída.</span><span class="sxs-lookup"><span data-stu-id="2745a-115">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="2745a-116">Další informace o tom, jak tomuto problému vyhnout, naleznete v tématu [řešení potíží s zděděné obslužných rutin událostí v jazyce Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="2745a-116">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2745a-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2745a-117">See Also</span></span>  
 [<span data-ttu-id="2745a-118">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="2745a-118">Inherits Statement</span></span>](~/docs/visual-basic/language-reference/statements/inherits-statement.md)  
 [<span data-ttu-id="2745a-119">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="2745a-119">Imports Statement (.NET Namespace and Type)</span></span>](~/docs/visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [<span data-ttu-id="2745a-120">using</span><span class="sxs-lookup"><span data-stu-id="2745a-120">using</span></span>](~/docs/csharp/language-reference/keywords/using.md)  
 [<span data-ttu-id="2745a-121">Účinky úpravy vzhledu základního formuláře</span><span class="sxs-lookup"><span data-stu-id="2745a-121">Effects of Modifying a Base Form's Appearance</span></span>](../../../../docs/framework/winforms/advanced/effects-of-modifying-base-form-appearance.md)  
 [<span data-ttu-id="2745a-122">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2745a-122">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)
