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
ms.openlocfilehash: 9bb6e6568822f3edcabf50a4fceb7cc6386f05ef
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45666509"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a><span data-ttu-id="2415e-102">Postupy: Používání modifikátorů a vlastností GenerateMember</span><span class="sxs-lookup"><span data-stu-id="2415e-102">How to: Use the Modifiers and GenerateMember Properties</span></span>
<span data-ttu-id="2415e-103">Umístíte-li komponenta ve formuláři Windows Forms, podle návrhu prostředí jsou k dispozici dvě vlastnosti: `GenerateMember` a `Modifiers`.</span><span class="sxs-lookup"><span data-stu-id="2415e-103">When you place a component on a Windows Form, two properties are provided by the design environment: `GenerateMember` and `Modifiers`.</span></span> <span data-ttu-id="2415e-104">`GenerateMember` Vlastnost určuje, když Návrhář formulářů Windows generuje členské proměnné pro komponentu.</span><span class="sxs-lookup"><span data-stu-id="2415e-104">The `GenerateMember` property specifies when the Windows Forms Designer generates a member variable for a component.</span></span> <span data-ttu-id="2415e-105">`Modifiers` Vlastnost je modifikátor přístupu, které jsou přiřazeny k této členské proměnné.</span><span class="sxs-lookup"><span data-stu-id="2415e-105">The `Modifiers` property is the access modifier assigned to that member variable.</span></span> <span data-ttu-id="2415e-106">Pokud hodnota `GenerateMember` vlastnost `false`, hodnota `Modifiers` vlastnost nemá žádný vliv.</span><span class="sxs-lookup"><span data-stu-id="2415e-106">If the value of the `GenerateMember` property is `false`, the value of the `Modifiers` property has no effect.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2415e-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="2415e-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="2415e-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="2415e-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="2415e-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="2415e-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-specify-whether-a-component-is-a-member-of-the-form"></a><span data-ttu-id="2415e-110">Chcete-li určit, zda je součást člena ve tvaru</span><span class="sxs-lookup"><span data-stu-id="2415e-110">To specify whether a component is a member of the form</span></span>  
  
1.  <span data-ttu-id="2415e-111">V Návrháři formulářů Windows otevřete formulář.</span><span class="sxs-lookup"><span data-stu-id="2415e-111">In the Windows Forms Designer, open your form.</span></span>  
  
2.  <span data-ttu-id="2415e-112">Otevřít **nástrojů**a ve formuláři, umístěte tři <xref:System.Windows.Forms.Button> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="2415e-112">Open the **Toolbox**, and on the form, place three <xref:System.Windows.Forms.Button> controls.</span></span>  
  
3.  <span data-ttu-id="2415e-113">Nastavte `GenerateMember` a `Modifiers` vlastnosti pro každý <xref:System.Windows.Forms.Button> ovládací prvek podle následující tabulky.</span><span class="sxs-lookup"><span data-stu-id="2415e-113">Set the `GenerateMember` and `Modifiers` properties for each <xref:System.Windows.Forms.Button> control according to the following table.</span></span>  
  
    |<span data-ttu-id="2415e-114">Název tlačítka</span><span class="sxs-lookup"><span data-stu-id="2415e-114">Button name</span></span>|<span data-ttu-id="2415e-115">Generatemember – hodnota</span><span class="sxs-lookup"><span data-stu-id="2415e-115">GenerateMember value</span></span>|<span data-ttu-id="2415e-116">Modifikátory hodnota</span><span class="sxs-lookup"><span data-stu-id="2415e-116">Modifiers value</span></span>|  
    |-----------------|--------------------------|---------------------|  
    |`button1`|`true`|`private`|  
    |`button2`|`true`|`protected`|  
    |`button3`|`false`|<span data-ttu-id="2415e-117">Žádné změny</span><span class="sxs-lookup"><span data-stu-id="2415e-117">No change</span></span>|  
  
4.  <span data-ttu-id="2415e-118">Sestavte řešení.</span><span class="sxs-lookup"><span data-stu-id="2415e-118">Build the solution.</span></span>  
  
5.  <span data-ttu-id="2415e-119">V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="2415e-119">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
6.  <span data-ttu-id="2415e-120">Otevřete **Form1** uzel a **Editor kódu**, otevřete **Form1.Designer.vb** nebo **Form1.Designer.cs** souboru.</span><span class="sxs-lookup"><span data-stu-id="2415e-120">Open the **Form1** node, and in the **Code Editor**,open the **Form1.Designer.vb** or **Form1.Designer.cs** file.</span></span> <span data-ttu-id="2415e-121">Tento soubor obsahuje kód, protože ho vygeneroval Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="2415e-121">This file contains the code emitted by the Windows Forms Designer.</span></span>  
  
7.  <span data-ttu-id="2415e-122">Najdete deklarace pro tři tlačítka.</span><span class="sxs-lookup"><span data-stu-id="2415e-122">Find the declarations for the three buttons.</span></span> <span data-ttu-id="2415e-123">Následující příklad kódu ukazuje rozdíly určené `GenerateMember` a `Modifiers` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2415e-123">The following code example shows the differences specified by the `GenerateMember` and `Modifiers` properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]  
  
     [!code-csharp[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]  
  
> [!NOTE]
>  <span data-ttu-id="2415e-124">Ve výchozím nastavení, Návrhář formulářů Windows přiřadí `private` (`Friend` v jazyce Visual Basic) modifikátor pro ovládací prvky kontejneru jako <xref:System.Windows.Forms.Panel>.</span><span class="sxs-lookup"><span data-stu-id="2415e-124">By default, the Windows Forms Designer assigns the `private` (`Friend` in Visual Basic) modifier to container controls like <xref:System.Windows.Forms.Panel>.</span></span> <span data-ttu-id="2415e-125">Pokud základním <xref:System.Windows.Forms.UserControl> nebo <xref:System.Windows.Forms.Form> má ovládací prvek kontejneru, nebude přijímat nové podřízené položky v zděděný ovládací prvky a formuláře.</span><span class="sxs-lookup"><span data-stu-id="2415e-125">If your base <xref:System.Windows.Forms.UserControl> or <xref:System.Windows.Forms.Form> has a container control, it will not accept new children in inherited controls and forms.</span></span> <span data-ttu-id="2415e-126">Řešením je změnit modifikátor základní kontejneru ovládacího prvku na `protected` nebo `public`.</span><span class="sxs-lookup"><span data-stu-id="2415e-126">The solution is to change the modifier of the base container control to `protected` or `public`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2415e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="2415e-127">See Also</span></span>  
 <xref:System.Windows.Forms.Button>  
 [<span data-ttu-id="2415e-128">Vizuální dědění modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2415e-128">Windows Forms Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [<span data-ttu-id="2415e-129">Návod: Demonstrace vizuálního dědění</span><span class="sxs-lookup"><span data-stu-id="2415e-129">Walkthrough: Demonstrating Visual Inheritance</span></span>](../../../../docs/framework/winforms/advanced/walkthrough-demonstrating-visual-inheritance.md)  
 [<span data-ttu-id="2415e-130">Postupy: Dědění v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2415e-130">How to: Inherit Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)
