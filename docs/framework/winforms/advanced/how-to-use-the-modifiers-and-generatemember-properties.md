---
title: 'Postupy: Používání modifikátorů a vlastností GenerateMember'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
ms.openlocfilehash: 451c54bf6272b4fbff46b5298ba5b6a9290656e8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523991"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="d827c-102">Postupy: Používání modifikátorů a vlastností GenerateMember</span><span class="sxs-lookup"><span data-stu-id="d827c-102">How to: Use the Modifiers and GenerateMember Properties</span></span>
<span data-ttu-id="d827c-103">Když umístíte komponentu ve formuláři Windows, dvě vlastnosti jsou k dispozici v prostředí návrhu: `GenerateMember` a `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="d827c-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="d827c-104">`GenerateMember` Vlastnost určuje, kdy Návrhář formulářů Windows generuje členské proměnné pro součást.</span><span class="sxs-lookup"><span data-stu-id="d827c-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="d827c-105">`Modifiers` Vlastnost je – modifikátor přístupu, které jsou přiřazeny k této proměnné členů.</span><span class="sxs-lookup"><span data-stu-id="d827c-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="d827c-106">Pokud hodnota `GenerateMember` vlastnost je `false`, hodnota `Modifiers` vlastnost nemá žádný efekt.</span><span class="sxs-lookup"><span data-stu-id="d827c-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d827c-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="d827c-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d827c-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="d827c-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d827c-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d827c-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="d827c-110">K určení, zda je součást členem formuláře</span><span class="sxs-lookup"><span data-stu-id="d827c-110">To specify whether a component is a member of the form</span></span>  
  
1.  <span data-ttu-id="d827c-111">V Návrháři formulářů Windows otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="d827c-111">In the Windows Forms Designer, open your form.</span></span>  
  
2.  <span data-ttu-id="d827c-112">Otevřete **sada nástrojů**a na formuláři, umístěte tři <xref:System.Windows.Forms.Button> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d827c-112">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
3.  <span data-ttu-id="d827c-113">Nastavte `GenerateMember` a `Modifiers` vlastnosti pro každou <xref:System.Windows.Forms.Button> řízení podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="d827c-113">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>  
  
    |<span data-ttu-id="d827c-114">Název tlačítka</span><span class="sxs-lookup"><span data-stu-id="d827c-114">Button name</span></span>|<span data-ttu-id="d827c-115">Generatemember – hodnota</span><span class="sxs-lookup"><span data-stu-id="d827c-115">GenerateMember value</span></span>|<span data-ttu-id="d827c-116">Modifikátory hodnota</span><span class="sxs-lookup"><span data-stu-id="d827c-116">Modifiers value</span></span>|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|<span data-ttu-id="d827c-117">Žádná změna</span><span class="sxs-lookup"><span data-stu-id="d827c-117">No change</span></span>|  
  
4.  <span data-ttu-id="d827c-118">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="d827c-118">Build the solution.</span></span>  
  
5.  <span data-ttu-id="d827c-119">V **Průzkumníku řešení**, klikněte **zobrazit všechny soubory** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="d827c-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
6.  <span data-ttu-id="d827c-120">Otevřete **Form1** uzel a v **Editor kódu**, otevřete **Form1.Designer.vb** nebo **Form1.Designer.cs** souboru.</span><span class="sxs-lookup"><span data-stu-id="d827c-120">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="d827c-121">Tento soubor obsahuje kód vysílaných Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="d827c-121">This file contains the code emitted by the Windows Forms Designer.</span></span>  
  
7.  <span data-ttu-id="d827c-122">Najít deklarace pro tři tlačítka.</span><span class="sxs-lookup"><span data-stu-id="d827c-122">Find the declarations for the three buttons.</span></span> <span data-ttu-id="d827c-123">Následující příklad kódu ukazuje rozdíly určeného `GenerateMember` a `Modifiers` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d827c-123">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  <span data-ttu-id="d827c-124">Ve výchozím nastavení, Návrhář formulářů Windows přiřadí `private` (`Friend` v jazyce Visual Basic) modifikátor pro ovládací prvky kontejneru jako <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="d827c-124">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="d827c-125">Pokud vaše základní <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Form> má ovládacího prvku kontejner nebude přijímat nové podřízených prvků ve formulářích a zděděné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="d827c-125">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="d827c-126">Řešení je změna modifikátor základní kontejneru ovládacího prvku na `protected` nebo `public`.</span><span class="sxs-lookup"><span data-stu-id="d827c-126">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d827c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="d827c-127">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="d827c-128">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d827c-128">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="d827c-129">Návod: Demonstrace vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="d827c-129">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [<span data-ttu-id="d827c-130">Postupy: Dědění v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d827c-130">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
