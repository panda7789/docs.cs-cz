---
title: 'Postupy: Dědění v modelu Windows Forms'
ms.date: 03/30/2017
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- inherited forms [Windows Forms], creating at run-time
- inheritance [Windows Forms], forms
- Windows Forms, inheritance
ms.assetid: cb3e1c0f-3d2a-4cdc-b0d1-c92eae567ffb
ms.openlocfilehash: a6d000bc853046cffbc2bddc54d1f5faec689032
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968617"
---
# <a name="how-to-inherit-windows-forms"></a><span data-ttu-id="e3d93-102">Postupy: Dědění v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3d93-102">How to: Inherit Windows Forms</span></span>

<span data-ttu-id="e3d93-103">Vytváření nových model Windows Forms děděním ze základních formulářů je praktický způsob, jak duplikovat vaše nejlepší úsilí, aniž byste museli projít celým procesem zcela znovu vytvořit formulář pokaždé, když ho budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="e3d93-103">Creating new Windows Forms by inheriting from base forms is a handy way to duplicate your best efforts without going through the process of entirely recreating a form every time you require it.</span></span>

<span data-ttu-id="e3d93-104">Další informace o dědění formulářů v době návrhu pomocí dialogového okna **Výběr dědičnosti** a o tom, jak vizuálně odlišit úrovně zabezpečení u zděděných ovládacích prvků [, naleznete v tématu How to: Dědění formulářů pomocí dialogového okna](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md)Výběr dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="e3d93-104">For more information about inheriting forms at design time using the **Inheritance Picker** dialog box and how to visually distinguish between security levels of inherited controls, see [How to: Inherit Forms Using the Inheritance Picker Dialog Box](how-to-inherit-forms-using-the-inheritance-picker-dialog-box.md).</span></span>

> [!NOTE]
> <span data-ttu-id="e3d93-105">Aby bylo možné dědit z formuláře, soubor nebo obor názvů obsahující tento formulář musí být integrovány do spustitelného souboru nebo knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="e3d93-105">In order to inherit from a form, the file or namespace containing that form must have been built into an executable file or DLL.</span></span> <span data-ttu-id="e3d93-106">Chcete-li sestavit projekt, v nabídce **sestavení** klikněte na příkaz **sestavit** .</span><span class="sxs-lookup"><span data-stu-id="e3d93-106">To build the project, choose **Build** from the **Build** menu.</span></span> <span data-ttu-id="e3d93-107">Také odkaz na obor názvů musí být přidán do třídy dědění formuláře.</span><span class="sxs-lookup"><span data-stu-id="e3d93-107">Also, a reference to the namespace must be added to the class inheriting the form.</span></span>

## <a name="inherit-a-form-programmatically"></a><span data-ttu-id="e3d93-108">Dědění formuláře prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="e3d93-108">Inherit a form programmatically</span></span>

1. <span data-ttu-id="e3d93-109">Ve třídě přidejte odkaz na obor názvů obsahující formulář, ze kterého chcete dědit.</span><span class="sxs-lookup"><span data-stu-id="e3d93-109">In your class, add a reference to the namespace containing the form you wish to inherit from.</span></span>

2. <span data-ttu-id="e3d93-110">V definici třídy přidejte odkaz na formulář, ze kterého se dědí.</span><span class="sxs-lookup"><span data-stu-id="e3d93-110">In the class definition, add a reference to the form to inherit from.</span></span> <span data-ttu-id="e3d93-111">Odkaz by měl zahrnovat obor názvů, který obsahuje formulář, následovaný tečkou, potom název základního formuláře samotného.</span><span class="sxs-lookup"><span data-stu-id="e3d93-111">The reference should include the namespace that contains the form, followed by a period, then the name of the base form itself.</span></span>

    ```vb
    Public Class Form2
        Inherits Namespace1.Form1
    ```

    ```csharp
    public class Form2 : Namespace1.Form1
    ```

 <span data-ttu-id="e3d93-112">Při dědění formulářů Pamatujte na to, že problémy mohou nastat s ohledem na obslužné rutiny událostí, které jsou volány dvakrát, protože každá událost je zpracovávána základní třídou a zděděnou třídou.</span><span class="sxs-lookup"><span data-stu-id="e3d93-112">When inheriting forms, keep in mind that issues may arise with regard to event handlers being called twice, because each event is being handled by both the base class and the inherited class.</span></span> <span data-ttu-id="e3d93-113">Další informace o tom, jak se vyhnout tomuto problému, najdete [v tématu řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="e3d93-113">For more information on how to avoid this problem, see [Troubleshooting Inherited Event Handlers in Visual Basic](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3d93-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3d93-114">See also</span></span>

- [<span data-ttu-id="e3d93-115">Příkaz Inherits</span><span class="sxs-lookup"><span data-stu-id="e3d93-115">Inherits Statement</span></span>](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [<span data-ttu-id="e3d93-116">Příkaz Imports (obor názvů a typ .NET)</span><span class="sxs-lookup"><span data-stu-id="e3d93-116">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="e3d93-117">using</span><span class="sxs-lookup"><span data-stu-id="e3d93-117">using</span></span>](../../../csharp/language-reference/keywords/using.md)
- [<span data-ttu-id="e3d93-118">Účinky úpravy vzhledu základního formuláře</span><span class="sxs-lookup"><span data-stu-id="e3d93-118">Effects of Modifying a Base Form's Appearance</span></span>](effects-of-modifying-base-form-appearance.md)
- [<span data-ttu-id="e3d93-119">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e3d93-119">Windows Forms Visual Inheritance</span></span>](windows-forms-visual-inheritance.md)
