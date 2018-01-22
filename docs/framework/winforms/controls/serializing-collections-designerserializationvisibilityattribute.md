---
title: "Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute"
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
- cpp
helpviewer_keywords:
- serialization [Windows Forms], collections
- standard types [Windows Forms], collections
- collections [Windows Forms], serializing
- collections [Windows Forms], standard types
ms.assetid: 020c9df4-fdc5-4dae-815a-963ecae5668c
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0267020f7e7a52e92b05a0bda0ee397e5c3393fc
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="c6a35-102">Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="c6a35-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>
<span data-ttu-id="c6a35-103">Vlastní ovládací prvky někdy zveřejní kolekci jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c6a35-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="c6a35-104">Tento návod ukazuje, jak používat <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> třída řídit, jak je kolekce serializovat v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="c6a35-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="c6a35-105">Použití <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> hodnotu pro vlastnost vaší kolekce zajistí, že vlastnost budou serializována.</span><span class="sxs-lookup"><span data-stu-id="c6a35-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>  
  
 <span data-ttu-id="c6a35-106">Zkopírujte kód v tomto tématu v jednom seznamu, najdete v části [postupy: serializace kolekcí z standardních typů s DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span><span class="sxs-lookup"><span data-stu-id="c6a35-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6a35-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="c6a35-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="c6a35-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="c6a35-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="c6a35-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="c6a35-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="c6a35-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6a35-110">Prerequisites</span></span>  
 <span data-ttu-id="c6a35-111">K dokončení tohoto návodu, budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="c6a35-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="c6a35-112">Dostatečná oprávnění, abyste mohli vytvořit a spustit projekty aplikací Windows Forms v počítači, kde je nainstalován Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6a35-112">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a><span data-ttu-id="c6a35-113">Vytvoření ovládacího prvku, který má serializovatelný kolekci</span><span class="sxs-lookup"><span data-stu-id="c6a35-113">Creating a Control That Has a Serializable Collection</span></span>  
 <span data-ttu-id="c6a35-114">Prvním krokem je vytvoření ovládacího prvku, který má kolekci serializovatelný jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c6a35-114">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="c6a35-115">Můžete upravit obsah této kolekce pomocí **Editor kolekce**, kterým můžete přistupovat z **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="c6a35-115">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a><span data-ttu-id="c6a35-116">Vytvoření ovládacího prvku s serializovatelný kolekcí</span><span class="sxs-lookup"><span data-stu-id="c6a35-116">To create a control with a serializable collection</span></span>  
  
1.  <span data-ttu-id="c6a35-117">Vytvoření projektu knihovny ovládacích prvků Windows názvem `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-117">Create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="c6a35-118">Další informace najdete v tématu [šablona knihovny ovládacího prvku Windows](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="c6a35-118">For more information, see [Windows Control Library Template](http://msdn.microsoft.com/library/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="c6a35-119">Přejmenování `UserControl1` k `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-119">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="c6a35-120">Další informace najdete v tématu [postupy: přejmenování identifikátory](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span><span class="sxs-lookup"><span data-stu-id="c6a35-120">For more information, see [How to: Rename Identifiers](http://msdn.microsoft.com/library/2430f732-2b70-4516-8cf6-a7bb71cc9724).</span></span>  
  
3.  <span data-ttu-id="c6a35-121">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> vlastnost `10`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-121">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>  
  
4.  <span data-ttu-id="c6a35-122">Místní <xref:System.Windows.Forms.TextBox> řídit ve `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-122">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>  
  
5.  <span data-ttu-id="c6a35-123">Vyberte <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a35-123">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="c6a35-124">V **vlastnosti** nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c6a35-124">In the **Properties** window, set the following properties.</span></span>  
  
    |<span data-ttu-id="c6a35-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c6a35-125">Property</span></span>|<span data-ttu-id="c6a35-126">Změňte na</span><span class="sxs-lookup"><span data-stu-id="c6a35-126">Change to</span></span>|  
    |--------------|---------------|  
    |<span data-ttu-id="c6a35-127">**Víceřádkového výrazu**</span><span class="sxs-lookup"><span data-stu-id="c6a35-127">**Multiline**</span></span>|`true`|  
    |<span data-ttu-id="c6a35-128">**Ukotvení**</span><span class="sxs-lookup"><span data-stu-id="c6a35-128">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |<span data-ttu-id="c6a35-129">**ScrollBars**</span><span class="sxs-lookup"><span data-stu-id="c6a35-129">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |<span data-ttu-id="c6a35-130">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="c6a35-130">**ReadOnly**</span></span>|`true`|  
  
6.  <span data-ttu-id="c6a35-131">V **Editor kódu**, deklarovat pole řetězce pole s názvem `stringsValue` v `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-131">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  <span data-ttu-id="c6a35-132">Definování `Strings` vlastnost `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-132">Define the `Strings` property on the `SerializationDemoControl`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6a35-133"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Hodnota slouží k povolení serializace kolekce.</span><span class="sxs-lookup"><span data-stu-id="c6a35-133">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  <span data-ttu-id="c6a35-134">Stiskněte klávesu F5, aby se projekt sestavil a spuštění vlastního ovládacího prvku v **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-134">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="c6a35-135">Najít `Strings` vlastnost <xref:System.Windows.Forms.PropertyGrid> z **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-135">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="c6a35-136">Klikněte na tlačítko `Strings` vlastnost, pak klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce řetězec**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-136">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="c6a35-137">Zadejte několik řetězců v **Editor kolekce řetězec**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-137">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="c6a35-138">Oddělte je stisknutím klávesy ENTER na konci každé řetězec.</span><span class="sxs-lookup"><span data-stu-id="c6a35-138">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="c6a35-139">Klikněte na tlačítko **OK** při zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="c6a35-139">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6a35-140">Zobrazí řetězce, které jste zadali v <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-140">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
## <a name="serializing-a-collection-property"></a><span data-ttu-id="c6a35-141">Serializace vlastnost kolekce</span><span class="sxs-lookup"><span data-stu-id="c6a35-141">Serializing a Collection Property</span></span>  
 <span data-ttu-id="c6a35-142">Chcete-li otestovat serializace chování ovládacího prvku, bude umístění ve formuláři a změňte obsah kolekce s **Editor kolekce**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-142">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="c6a35-143">Zobrazí stav serializovaných kolekce prohlížením speciální návrháře souboru, do kterého **Návrhář formulářů Windows** vysílá kódu.</span><span class="sxs-lookup"><span data-stu-id="c6a35-143">You can see the serialized collection state by looking at a special designer file, into which the **Windows Forms Designer** emits code.</span></span>  
  
#### <a name="to-serialize-a-collection"></a><span data-ttu-id="c6a35-144">K serializaci kolekce</span><span class="sxs-lookup"><span data-stu-id="c6a35-144">To serialize a collection</span></span>  
  
1.  <span data-ttu-id="c6a35-145">Přidejte projekt aplikace Windows k řešení.</span><span class="sxs-lookup"><span data-stu-id="c6a35-145">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="c6a35-146">Název projektu `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-146">Name the project `SerializationDemoControlTest`.</span></span>  
  
2.  <span data-ttu-id="c6a35-147">V **sada nástrojů**, najít na kartě s názvem **SerializationDemoControlLib součásti**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-147">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="c6a35-148">Na této kartě můžete najít `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-148">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="c6a35-149">Další informace najdete v tématu [návod: Automatické vyplnění nástrojů s komponentami vlastní](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="c6a35-149">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
3.  <span data-ttu-id="c6a35-150">Místní `SerializationDemoControl` ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="c6a35-150">Place a `SerializationDemoControl` on your form.</span></span>  
  
4.  <span data-ttu-id="c6a35-151">Najít `Strings` vlastnost **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="c6a35-151">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="c6a35-152">Klikněte na tlačítko `Strings` vlastnost, pak klikněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton – snímek obrazovky](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce řetězec**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-152">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="c6a35-153">Zadejte několik řetězců v **Editor kolekce řetězec**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-153">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="c6a35-154">Oddělte je stisknutím klávesy ENTER na konci každé řetězec.</span><span class="sxs-lookup"><span data-stu-id="c6a35-154">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="c6a35-155">Klikněte na tlačítko **OK** při zadání řetězce.</span><span class="sxs-lookup"><span data-stu-id="c6a35-155">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6a35-156">Zobrazí řetězce, které jste zadali v <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-156">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
1.  <span data-ttu-id="c6a35-157">V **Průzkumníku řešení**, klikněte **zobrazit všechny soubory** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="c6a35-157">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
2.  <span data-ttu-id="c6a35-158">Otevřete **Form1** uzlu.</span><span class="sxs-lookup"><span data-stu-id="c6a35-158">Open the **Form1** node.</span></span> <span data-ttu-id="c6a35-159">Ybrat je do souboru s názvem **Form1.Designer.cs** nebo **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-159">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="c6a35-160">Toto je soubor, do kterého **Návrhář formulářů Windows** vysílá kód představující stav návrhu a jeho podřízených ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="c6a35-160">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="c6a35-161">Otevřete tento soubor **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-161">Open this file in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="c6a35-162">Otevřete oblast názvem **Windows Form Designer generovaného kódu** a najděte část s názvem bez přípony **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="c6a35-162">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="c6a35-163">Pod tímto štítkem je kód představující serializovaný stav ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c6a35-163">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="c6a35-164">Zobrazí řetězce, které jste zadali v kroku 5 v přiřazení k `Strings` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c6a35-164">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="c6a35-165">Následující příklady kódu v C# a Visual Basic, zobrazí podobná co se zobrazí pokud jste zadali řetězce "red", "oranžové" a "žlutý" code.</span><span class="sxs-lookup"><span data-stu-id="c6a35-165">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  <span data-ttu-id="c6a35-166">V **Editor kódu**, změňte hodnotu <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` vlastnost <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="c6a35-166">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. <span data-ttu-id="c6a35-167">Znovu sestavte řešení a zopakujte kroky 3 a 4.</span><span class="sxs-lookup"><span data-stu-id="c6a35-167">Rebuild the solution and repeat steps 3 and 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c6a35-168">V takovém případě **Návrhář formulářů Windows** vysílá žádné přiřazení `Strings` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c6a35-168">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="c6a35-169">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c6a35-169">Next Steps</span></span>  
 <span data-ttu-id="c6a35-170">Jakmile budete vědět, jak k serializaci kolekce standardní typy, vezměte v úvahu integraci vaše vlastní ovládací prvky hlubšímu do prostředí návrhu.</span><span class="sxs-lookup"><span data-stu-id="c6a35-170">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="c6a35-171">Následující témata popisují postup rozšíření integrace návrhu pro vaše vlastní ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="c6a35-171">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>  
  
-   [<span data-ttu-id="c6a35-172">Architektura pro návrh</span><span class="sxs-lookup"><span data-stu-id="c6a35-172">Design-Time Architecture</span></span>](http://msdn.microsoft.com/library/4881917b-628f-4689-b872-472e4f8a4e3a)  
  
-   [<span data-ttu-id="c6a35-173">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c6a35-173">Attributes in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/attributes-in-windows-forms-controls.md)  
  
-   [<span data-ttu-id="c6a35-174">Přehled Návrháře serializace</span><span class="sxs-lookup"><span data-stu-id="c6a35-174">Designer Serialization Overview</span></span>](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
  
-   [<span data-ttu-id="c6a35-175">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="c6a35-175">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](../../../../docs/framework/winforms/controls/creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a><span data-ttu-id="c6a35-176">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6a35-176">See Also</span></span>  
 <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>  
 [<span data-ttu-id="c6a35-177">Přehled Návrháře serializace</span><span class="sxs-lookup"><span data-stu-id="c6a35-177">Designer Serialization Overview</span></span>](http://msdn.microsoft.com/library/c342635a-aa5f-4281-915b-b013738af15a)  
 [<span data-ttu-id="c6a35-178">Postupy: serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="c6a35-178">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](http://msdn.microsoft.com/library/7829fcdd-8205-405f-8231-a1282a9835c9)  
 [<span data-ttu-id="c6a35-179">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="c6a35-179">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
