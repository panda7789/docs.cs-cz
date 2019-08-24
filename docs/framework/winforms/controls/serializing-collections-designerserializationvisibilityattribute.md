---
title: 'Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute'
ms.date: 03/30/2017
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2fbb0715d148b443b1eca8f400e4ad43eb51fa43
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015737"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a><span data-ttu-id="b6895-102">Návod: Serializace kolekcí standardních typů</span><span class="sxs-lookup"><span data-stu-id="b6895-102">Walkthrough: Serialize collections of standard types</span></span>

<span data-ttu-id="b6895-103">Vaše vlastní ovládací prvky budou někdy vystavovat kolekci jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b6895-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="b6895-104">Tento návod ukazuje, jak použít <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> třídu pro řízení způsobu serializace kolekce v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="b6895-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="b6895-105"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Použití hodnoty na vlastnost kolekce zajistí, že bude vlastnost serializována.</span><span class="sxs-lookup"><span data-stu-id="b6895-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="b6895-106">Postup kopírování kódu v tomto tématu jako jediného výpisu naleznete v [tématu How to: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="b6895-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b6895-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6895-107">Prerequisites</span></span>

<span data-ttu-id="b6895-108">K dokončení tohoto Názorného postupu potřebujete Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b6895-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="b6895-109">Vytvoření ovládacího prvku s serializovatelný kolekcí</span><span class="sxs-lookup"><span data-stu-id="b6895-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="b6895-110">Prvním krokem je vytvoření ovládacího prvku, který má serializovatelné kolekce jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b6895-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="b6895-111">Obsah této kolekce můžete upravit pomocí **editoru kolekce**, ke kterému můžete přistupovat z okna **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="b6895-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="b6895-112">V aplikaci Visual Studio vytvořte projekt knihovny ovládacích prvků systému Windows a pojmenujte jej **SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="b6895-112">In Visual Studio, create a Windows Control Library project, and name it **SerializationDemoControlLib**.</span></span>

2. <span data-ttu-id="b6895-113">Přejmenujte `UserControl1` na `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="b6895-113">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="b6895-114">Další informace najdete v tématu [přejmenování refaktoringu symbolů kódu](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="b6895-114">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="b6895-115">V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> vlastnosti na hodnotu **10**.</span><span class="sxs-lookup"><span data-stu-id="b6895-115">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to **10**.</span></span>

4. <span data-ttu-id="b6895-116">Umístěte ovládací prvek do `SerializationDemoControl`. <xref:System.Windows.Forms.TextBox></span><span class="sxs-lookup"><span data-stu-id="b6895-116">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="b6895-117"><xref:System.Windows.Forms.TextBox> Vyberte ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b6895-117">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="b6895-118">V okně **vlastnosti** nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6895-118">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="b6895-119">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="b6895-119">Property</span></span>|<span data-ttu-id="b6895-120">Změnit na</span><span class="sxs-lookup"><span data-stu-id="b6895-120">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="b6895-121">**Víceřádkový**</span><span class="sxs-lookup"><span data-stu-id="b6895-121">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="b6895-122">**Vyjměte**</span><span class="sxs-lookup"><span data-stu-id="b6895-122">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="b6895-123">**Posuvníky**</span><span class="sxs-lookup"><span data-stu-id="b6895-123">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="b6895-124">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="b6895-124">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="b6895-125">V **editoru kódu**deklarujte pole řetězců s názvem `stringsValue` v. `SerializationDemoControl`</span><span class="sxs-lookup"><span data-stu-id="b6895-125">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="b6895-126">`Strings` Definujte vlastnost`SerializationDemoControl`na.</span><span class="sxs-lookup"><span data-stu-id="b6895-126">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b6895-127"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Hodnota se používá k povolení serializace kolekce.</span><span class="sxs-lookup"><span data-stu-id="b6895-127">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="b6895-128">Stisknutím klávesy **F5** Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="b6895-128">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="b6895-129">V<xref:System.Windows.Forms.PropertyGrid> **kontejneru testu UserControl**vyhledejte vlastnost Strings.</span><span class="sxs-lookup"><span data-stu-id="b6895-129">Find the **Strings** property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="b6895-130">Vyberte vlastnost **řetězce** a potom vyberte tři tečky (![tři tečky (...) v okno Vlastnosti sadě Visual Studio](./media/visual-studio-ellipsis-button.png)) a otevřete **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="b6895-130">Select the **Strings** property, then select the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="b6895-131">V **editoru kolekce řetězců**zadejte několik řetězců.</span><span class="sxs-lookup"><span data-stu-id="b6895-131">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="b6895-132">Oddělte je stisknutím klávesy **ENTER** na konci každého řetězce.</span><span class="sxs-lookup"><span data-stu-id="b6895-132">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="b6895-133">Po dokončení zadávání řetězců klikněte na **OK** .</span><span class="sxs-lookup"><span data-stu-id="b6895-133">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b6895-134">Řetězce, které jste zadali, se <xref:System.Windows.Forms.TextBox> zobrazí v `SerializationDemoControl`části.</span><span class="sxs-lookup"><span data-stu-id="b6895-134">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serialize-a-collection-property"></a><span data-ttu-id="b6895-135">Serializace vlastnosti kolekce</span><span class="sxs-lookup"><span data-stu-id="b6895-135">Serialize a collection property</span></span>

<span data-ttu-id="b6895-136">Chcete-li otestovat chování serializace ovládacího prvku, umístěte ho do formuláře a změňte obsah kolekce pomocí **editoru kolekce**.</span><span class="sxs-lookup"><span data-stu-id="b6895-136">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="b6895-137">Serializovaný stav shromažďování můžete zobrazit tak, že prohlížíte speciální soubor návrháře, do kterého **Návrhář formulářů** generuje kód.</span><span class="sxs-lookup"><span data-stu-id="b6895-137">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

1. <span data-ttu-id="b6895-138">Přidejte do řešení projekt aplikace pro Windows.</span><span class="sxs-lookup"><span data-stu-id="b6895-138">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="b6895-139">Pojmenujte `SerializationDemoControlTest`projekt.</span><span class="sxs-lookup"><span data-stu-id="b6895-139">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="b6895-140">V **sadě nástrojů**Najděte kartu s názvem **součásti SerializationDemoControlLib**.</span><span class="sxs-lookup"><span data-stu-id="b6895-140">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="b6895-141">Na této kartě najdete `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="b6895-141">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="b6895-142">Další informace najdete v tématu [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="b6895-142">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="b6895-143">Umístěte objekt `SerializationDemoControl` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="b6895-143">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="b6895-144">V okně **vlastnosti** vyhledejte vlastnost.`Strings`</span><span class="sxs-lookup"><span data-stu-id="b6895-144">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="b6895-145">Klikněte na![](./media/visual-studio-ellipsis-button.png)vlastnost a potom kliknutím na tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.) otevřete **Editor kolekce řetězců.** `Strings`</span><span class="sxs-lookup"><span data-stu-id="b6895-145">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="b6895-146">Zadejte několik řetězců v **editoru kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="b6895-146">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="b6895-147">Oddělte je stisknutím klávesy **ENTER** na konci každého řetězce.</span><span class="sxs-lookup"><span data-stu-id="b6895-147">Separate them by pressing **Enter** at the end of each string.</span></span> <span data-ttu-id="b6895-148">Po dokončení zadávání řetězců klikněte na **OK** .</span><span class="sxs-lookup"><span data-stu-id="b6895-148">Click **OK** when you are finished entering strings.</span></span>

> [!NOTE]
> <span data-ttu-id="b6895-149">Řetězce, které jste zadali, se <xref:System.Windows.Forms.TextBox> zobrazí v `SerializationDemoControl`části.</span><span class="sxs-lookup"><span data-stu-id="b6895-149">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

6. <span data-ttu-id="b6895-150">V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .</span><span class="sxs-lookup"><span data-stu-id="b6895-150">In **Solution Explorer**, click the **Show All Files** button.</span></span>

7. <span data-ttu-id="b6895-151">Otevřete uzel **Form1** .</span><span class="sxs-lookup"><span data-stu-id="b6895-151">Open the **Form1** node.</span></span> <span data-ttu-id="b6895-152">Pod ním je soubor s názvem **Form1.Designer.cs** nebo **Form1. Designer. vb**.</span><span class="sxs-lookup"><span data-stu-id="b6895-152">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="b6895-153">Jedná se o soubor, do kterého **Návrhář formulářů** emituje kód, který představuje stav při návrhu formuláře a jeho podřízených ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="b6895-153">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="b6895-154">Otevřete tento soubor v **editoru kódu**.</span><span class="sxs-lookup"><span data-stu-id="b6895-154">Open this file in the **Code Editor**.</span></span>

8. <span data-ttu-id="b6895-155">Otevřete oblast nazvanou **Windows Form Designer generovaný kód** a najděte oddíl označený **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="b6895-155">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="b6895-156">Pod tímto popiskem je kód představující serializovaný stav vašeho ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b6895-156">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="b6895-157">Řetězce, které jste zadali v kroku 5, se zobrazí v přiřazení `Strings` k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6895-157">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="b6895-158">Následující příklady kódu v C# a Visual Basic ukazují kód podobný tomu, co se vám zobrazí, pokud jste zadali řetězce "Red", "oranžová" a "žlutá".</span><span class="sxs-lookup"><span data-stu-id="b6895-158">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. <span data-ttu-id="b6895-159">V **editoru kódu**změňte hodnotu <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> `Strings` vlastnosti <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>na.</span><span class="sxs-lookup"><span data-stu-id="b6895-159">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. <span data-ttu-id="b6895-160">Znovu sestavte řešení a opakujte kroky 3 a 4.</span><span class="sxs-lookup"><span data-stu-id="b6895-160">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="b6895-161">V takovém případě **Návrhář formulářů** negeneruje žádné přiřazení k `Strings` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b6895-161">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="b6895-162">Další postup</span><span class="sxs-lookup"><span data-stu-id="b6895-162">Next steps</span></span>

<span data-ttu-id="b6895-163">Jakmile se dozvíte, jak serializovat kolekci standardních typů, zvažte integraci vlastních ovládacích prvků do prostředí v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="b6895-163">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="b6895-164">Následující témata popisují, jak vylepšit integraci vlastních ovládacích prvků v době návrhu:</span><span class="sxs-lookup"><span data-stu-id="b6895-164">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="b6895-165">[Architektura v době návrhu](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="b6895-165">[Design-Time Architecture](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="b6895-166">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b6895-166">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="b6895-167">[Přehled serializace návrháře](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="b6895-167">[Designer Serialization Overview](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="b6895-168">Návod: Vytvoření ovládacího prvku model Windows Forms, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="b6895-168">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="b6895-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6895-169">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [<span data-ttu-id="b6895-170">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="b6895-170">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
