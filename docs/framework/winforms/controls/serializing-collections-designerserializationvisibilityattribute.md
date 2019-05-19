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
ms.openlocfilehash: 1f1412f03f912c0142b08d5ad8581e421252cfb3
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882362"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="9c6d0-102">Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="9c6d0-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>

<span data-ttu-id="9c6d0-103">Vlastní ovládací prvky se někdy vystavit kolekci jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="9c6d0-104">Tento návod ukazuje, jak používat <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> třídy řídit, jak je kolekce serializovat v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="9c6d0-105">Použití <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> hodnota k vaší kolekci vlastností zajišťuje, že vlastnost bude serializována.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>

<span data-ttu-id="9c6d0-106">Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="9c6d0-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9c6d0-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c6d0-107">Prerequisites</span></span>

<span data-ttu-id="9c6d0-108">Visual Studio k dokončení tohoto návodu potřebujete.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-108">You need Visual Studio to complete this walkthrough.</span></span>

## <a name="create-a-control-with-a-serializable-collection"></a><span data-ttu-id="9c6d0-109">Vytvoření ovládacího prvku s serializovatelný kolekcí</span><span class="sxs-lookup"><span data-stu-id="9c6d0-109">Create a control with a serializable collection</span></span>

<span data-ttu-id="9c6d0-110">Prvním krokem je vytvoření ovládacího prvku, který má kolekci serializovat jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-110">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="9c6d0-111">Můžete upravit obsah této kolekce pomocí **Editor kolekce**, která je přístupná z **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-111">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>

1. <span data-ttu-id="9c6d0-112">V sadě Visual Studio vytvořte projekt knihovny ovládacích prvků Windows s názvem `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-112">In Visual Studio, create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="9c6d0-113">Další informace najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9c6d0-113">For more information, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>

2. <span data-ttu-id="9c6d0-114">Přejmenovat `UserControl1` k `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-114">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="9c6d0-115">Další informace najdete v tématu [kódu symbol refaktoring pro přejmenování](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="9c6d0-115">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>

3. <span data-ttu-id="9c6d0-116">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> vlastnost `10`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-116">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>

4. <span data-ttu-id="9c6d0-117">Místo <xref:System.Windows.Forms.TextBox> v ovládacím prvku `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-117">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>

5. <span data-ttu-id="9c6d0-118">Vyberte <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-118">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="9c6d0-119">V **vlastnosti** okno, nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-119">In the **Properties** window, set the following properties.</span></span>

    |<span data-ttu-id="9c6d0-120">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="9c6d0-120">Property</span></span>|<span data-ttu-id="9c6d0-121">Změňte na</span><span class="sxs-lookup"><span data-stu-id="9c6d0-121">Change to</span></span>|
    |--------------|---------------|
    |<span data-ttu-id="9c6d0-122">**Multiline**</span><span class="sxs-lookup"><span data-stu-id="9c6d0-122">**Multiline**</span></span>|`true`|
    |<span data-ttu-id="9c6d0-123">**Ukotvení**</span><span class="sxs-lookup"><span data-stu-id="9c6d0-123">**Dock**</span></span>|<xref:System.Windows.Forms.DockStyle.Fill>|
    |<span data-ttu-id="9c6d0-124">**ScrollBars**</span><span class="sxs-lookup"><span data-stu-id="9c6d0-124">**ScrollBars**</span></span>|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |<span data-ttu-id="9c6d0-125">**ReadOnly**</span><span class="sxs-lookup"><span data-stu-id="9c6d0-125">**ReadOnly**</span></span>|`true`|

6. <span data-ttu-id="9c6d0-126">V **Editor kódu**, deklarace pole pole řetězce s názvem `stringsValue` v `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-126">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. <span data-ttu-id="9c6d0-127">Definovat `Strings` vlastnost `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-127">Define the `Strings` property on the `SerializationDemoControl`.</span></span>

   > [!NOTE]
   > <span data-ttu-id="9c6d0-128"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Hodnota se používá k povolení serializace kolekce.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-128">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. <span data-ttu-id="9c6d0-129">Stisknutím klávesy **F5** se projekt sestavil a spouštění ovládacího prvku v **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-129">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span>

9. <span data-ttu-id="9c6d0-130">Najít `Strings` vlastnost <xref:System.Windows.Forms.PropertyGrid> z **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-130">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="9c6d0-131">Klikněte na tlačítko `Strings` vlastnost, klepněte na tlačítko se třemi tečkami (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) tlačítko Otevřít **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-131">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

10. <span data-ttu-id="9c6d0-132">Zadejte několik řetězců v **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-132">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="9c6d0-133">Oddělte je stisknutím klávesy **Enter** klíče na konci každého řetězce.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-133">Separate them by pressing the **Enter** key at the end of each string.</span></span> <span data-ttu-id="9c6d0-134">Klikněte na tlačítko **OK** po dokončení zadávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-134">Click **OK** when you are finished entering strings.</span></span>

   > [!NOTE]
   > <span data-ttu-id="9c6d0-135">Zobrazí řetězce jste zadali v <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-135">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

## <a name="serializing-a-collection-property"></a><span data-ttu-id="9c6d0-136">Serializace vlastnost kolekce</span><span class="sxs-lookup"><span data-stu-id="9c6d0-136">Serializing a Collection Property</span></span>

<span data-ttu-id="9c6d0-137">K otestování chování serializace ovládacího prvku, umístěte ho na formuláři a změnit obsah kolekce s **Editor kolekce**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-137">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="9c6d0-138">Zobrazí se stav serializovaná shromažďování zobrazením zvláštní soubor návrháře, do kterého **Návrháře formulářů Windows** emituje kód.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-138">You can see the serialized collection state by looking at a special designer file into which the **Windows Forms Designer** emits code.</span></span>

### <a name="to-serialize-a-collection"></a><span data-ttu-id="9c6d0-139">K serializaci kolekce</span><span class="sxs-lookup"><span data-stu-id="9c6d0-139">To serialize a collection</span></span>

1. <span data-ttu-id="9c6d0-140">Přidáte do řešení projekt aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-140">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="9c6d0-141">Pojmenujte projekt `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-141">Name the project `SerializationDemoControlTest`.</span></span>

2. <span data-ttu-id="9c6d0-142">V **nástrojů**, najít na kartě s názvem **SerializationDemoControlLib komponenty**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-142">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="9c6d0-143">Na této kartě můžete najít `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-143">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="9c6d0-144">Další informace najdete v tématu [názorný postup: Automatické vyplnění nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="9c6d0-144">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>

3. <span data-ttu-id="9c6d0-145">Místo `SerializationDemoControl` na formuláři.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-145">Place a `SerializationDemoControl` on your form.</span></span>

4. <span data-ttu-id="9c6d0-146">Najít `Strings` vlastnost **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-146">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="9c6d0-147">Klikněte na tlačítko `Strings` vlastnost, klepněte na tlačítko se třemi tečkami (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/visual-studio-ellipsis-button.png)) tlačítko Otevřít **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-147">Click the `Strings` property, then click the ellipsis (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/visual-studio-ellipsis-button.png)) button to open the **String Collection Editor**.</span></span>

5. <span data-ttu-id="9c6d0-148">Zadejte několik řetězců v **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-148">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="9c6d0-149">Oddělte je stisknutím klávesy ENTER na konci každého řetězce.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-149">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="9c6d0-150">Klikněte na tlačítko **OK** po dokončení zadávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-150">Click **OK** when you are finished entering strings.</span></span>

> [!NOTE]
> <span data-ttu-id="9c6d0-151">Zobrazí řetězce jste zadali v <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-151">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>

1. <span data-ttu-id="9c6d0-152">V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-152">In **Solution Explorer**, click the **Show All Files** button.</span></span>

2. <span data-ttu-id="9c6d0-153">Otevřít **Form1** uzlu.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-153">Open the **Form1** node.</span></span> <span data-ttu-id="9c6d0-154">Rat je soubor s názvem **Form1.Designer.cs** nebo **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-154">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="9c6d0-155">Jedná se o soubor, do kterého **Návrháře formulářů Windows** emituje kód představující stav návrhu a jeho podřízených ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-155">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="9c6d0-156">Tento soubor otevřít v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-156">Open this file in the **Code Editor**.</span></span>

3. <span data-ttu-id="9c6d0-157">Otevřete oblast volá **kód generovaný návrhářem formulářů Windows** a vyhledejte část s názvem **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-157">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="9c6d0-158">Pod tento popisek je kód představující serializovaný stav ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-158">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="9c6d0-159">Řetězce, které jste zadali v kroku 5 jsou zobrazeny v přiřazení k `Strings` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-159">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="9c6d0-160">Následující příklady kódu v C# a Visual Basic, zobrazit kód podobný co se zobrazí pokud jste zadali řetězce "red", "oranžové" a "žlutý".</span><span class="sxs-lookup"><span data-stu-id="9c6d0-160">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

4. <span data-ttu-id="9c6d0-161">V **Editor kódu**, změňte hodnotu <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` vlastnost <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-161">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

5. <span data-ttu-id="9c6d0-162">Znovu sestavte řešení a zopakujte kroky 3 a 4.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-162">Rebuild the solution and repeat steps 3 and 4.</span></span>

> [!NOTE]
> <span data-ttu-id="9c6d0-163">V takovém případě **Návrháře formulářů Windows** vysílá žádné přiřazení `Strings` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-163">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9c6d0-164">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9c6d0-164">Next Steps</span></span>

<span data-ttu-id="9c6d0-165">Když víte, jak serializace kolekcí standardních typů, vezměte v úvahu integrace vlastních ovládacích prvků hlouběji do návrhové prostředí.</span><span class="sxs-lookup"><span data-stu-id="9c6d0-165">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="9c6d0-166">Následující témata popisují, jak vylepšit návrhu integrace vlastních ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="9c6d0-166">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>

- <span data-ttu-id="9c6d0-167">[Architektura návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9c6d0-167">[Design-Time Architecture](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))</span></span>

- [<span data-ttu-id="9c6d0-168">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c6d0-168">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)

- <span data-ttu-id="9c6d0-169">[Přehled serializace návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9c6d0-169">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>

- [<span data-ttu-id="9c6d0-170">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio Design-Time</span><span class="sxs-lookup"><span data-stu-id="9c6d0-170">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a><span data-ttu-id="9c6d0-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c6d0-171">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- <span data-ttu-id="9c6d0-172">[Přehled serializace návrháře](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9c6d0-172">[Designer Serialization Overview](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))</span></span>
- <span data-ttu-id="9c6d0-173">[Postupy: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="9c6d0-173">[How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))</span></span>
- [<span data-ttu-id="9c6d0-174">Návod: Automatické vyplnění nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="9c6d0-174">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
