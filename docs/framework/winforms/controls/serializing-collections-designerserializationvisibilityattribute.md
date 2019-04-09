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
ms.openlocfilehash: 04eb56fe78aa2d9ef5ab0daae4ba1c873cfc2b26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097756"
---
# <a name="walkthrough-serializing-collections-of-standard-types-with-the-designerserializationvisibilityattribute"></a><span data-ttu-id="babbf-102">Návod: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="babbf-102">Walkthrough: Serializing Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>
<span data-ttu-id="babbf-103">Vlastní ovládací prvky se někdy vystavit kolekci jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="babbf-103">Your custom controls will sometimes expose a collection as a property.</span></span> <span data-ttu-id="babbf-104">Tento návod ukazuje, jak používat <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> třídy řídit, jak je kolekce serializovat v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="babbf-104">This walkthrough demonstrates how to use the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> class to control how a collection is serialized at design time.</span></span> <span data-ttu-id="babbf-105">Použití <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> hodnota k vaší kolekci vlastností zajišťuje, že vlastnost bude serializována.</span><span class="sxs-lookup"><span data-stu-id="babbf-105">Applying the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value to your collection property ensures that the property will be serialized.</span></span>  
  
 <span data-ttu-id="babbf-106">Pokud chcete zkopírovat kód v tomto tématu jako jeden seznam, naleznete v tématu [jak: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span><span class="sxs-lookup"><span data-stu-id="babbf-106">To copy the code in this topic as a single listing, see [How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babbf-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="babbf-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="babbf-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="babbf-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="babbf-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="babbf-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="babbf-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="babbf-110">Prerequisites</span></span>  
 <span data-ttu-id="babbf-111">K dokončení tohoto návodu budete potřebovat:</span><span class="sxs-lookup"><span data-stu-id="babbf-111">In order to complete this walkthrough, you will need:</span></span>  
  
-   <span data-ttu-id="babbf-112">Dostatečná oprávnění k vytvoření a spuštění projektů aplikace Windows Forms v počítači nainstalovanou aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="babbf-112">Sufficient permissions to be able to create and run Windows Forms application projects on the computer where Visual Studio is installed.</span></span>  
  
## <a name="creating-a-control-that-has-a-serializable-collection"></a><span data-ttu-id="babbf-113">Vytvoření ovládacího prvku, který je serializovatelný kolekce</span><span class="sxs-lookup"><span data-stu-id="babbf-113">Creating a Control That Has a Serializable Collection</span></span>  
 <span data-ttu-id="babbf-114">Prvním krokem je vytvoření ovládacího prvku, který má kolekci serializovat jako vlastnost.</span><span class="sxs-lookup"><span data-stu-id="babbf-114">The first step is to create a control that has a serializable collection as a property.</span></span> <span data-ttu-id="babbf-115">Můžete upravit obsah této kolekce pomocí **Editor kolekce**, která je přístupná z **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="babbf-115">You can edit the contents of this collection using the **Collection Editor**, which you can access from the **Properties** window.</span></span>  
  
#### <a name="to-create-a-control-with-a-serializable-collection"></a><span data-ttu-id="babbf-116">Vytvoření ovládacího prvku s serializovatelný kolekcí</span><span class="sxs-lookup"><span data-stu-id="babbf-116">To create a control with a serializable collection</span></span>  
  
1.  <span data-ttu-id="babbf-117">Vytvořit projekt Knihovna ovládacích prvků Windows s názvem `SerializationDemoControlLib`.</span><span class="sxs-lookup"><span data-stu-id="babbf-117">Create a Windows Control Library project called `SerializationDemoControlLib`.</span></span> <span data-ttu-id="babbf-118">Další informace najdete v tématu [šablonu ovládacího prvku knihovny Windows](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="babbf-118">For more information, see [Windows Control Library Template](https://docs.microsoft.com/previous-versions/kxczf775(v=vs.100)).</span></span>  
  
2.  <span data-ttu-id="babbf-119">Přejmenovat `UserControl1` k `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="babbf-119">Rename `UserControl1` to `SerializationDemoControl`.</span></span> <span data-ttu-id="babbf-120">Další informace najdete v tématu [kódu symbol refaktoring pro přejmenování](/visualstudio/ide/reference/rename).</span><span class="sxs-lookup"><span data-stu-id="babbf-120">For more information, see [Rename a code symbol refactoring](/visualstudio/ide/reference/rename).</span></span>  
  
3.  <span data-ttu-id="babbf-121">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> vlastnost `10`.</span><span class="sxs-lookup"><span data-stu-id="babbf-121">In the **Properties** window, set the value of the <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> property to `10`.</span></span>  
  
4.  <span data-ttu-id="babbf-122">Místo <xref:System.Windows.Forms.TextBox> v ovládacím prvku `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="babbf-122">Place a <xref:System.Windows.Forms.TextBox> control in the `SerializationDemoControl`.</span></span>  
  
5.  <span data-ttu-id="babbf-123">Vyberte <xref:System.Windows.Forms.TextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="babbf-123">Select the <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="babbf-124">V **vlastnosti** okno, nastavte následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="babbf-124">In the **Properties** window, set the following properties.</span></span>  
  
    |<span data-ttu-id="babbf-125">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="babbf-125">Property</span></span>|<span data-ttu-id="babbf-126">Změňte na</span><span class="sxs-lookup"><span data-stu-id="babbf-126">Change to</span></span>|  
    |--------------|---------------|  
    |**<span data-ttu-id="babbf-127">Multiline</span><span class="sxs-lookup"><span data-stu-id="babbf-127">Multiline</span></span>**|`true`|  
    |**<span data-ttu-id="babbf-128">Ukotvení</span><span class="sxs-lookup"><span data-stu-id="babbf-128">Dock</span></span>**|<xref:System.Windows.Forms.DockStyle.Fill>|  
    |**<span data-ttu-id="babbf-129">ScrollBars</span><span class="sxs-lookup"><span data-stu-id="babbf-129">ScrollBars</span></span>**|<xref:System.Windows.Forms.ScrollBars.Vertical>|  
    |**<span data-ttu-id="babbf-130">ReadOnly</span><span class="sxs-lookup"><span data-stu-id="babbf-130">ReadOnly</span></span>**|`true`|  
  
6.  <span data-ttu-id="babbf-131">V **Editor kódu**, deklarace pole pole řetězce s názvem `stringsValue` v `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="babbf-131">In the **Code Editor**, declare a string array field named `stringsValue` in `SerializationDemoControl`.</span></span>  
  
     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]  
  
7.  <span data-ttu-id="babbf-132">Definovat `Strings` vlastnost `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="babbf-132">Define the `Strings` property on the `SerializationDemoControl`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babbf-133"><xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Hodnota se používá k povolení serializace kolekce.</span><span class="sxs-lookup"><span data-stu-id="babbf-133">The <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> value is used to enable serialization of the collection.</span></span>  
  
 [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
 [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
 [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]  
  
1.  <span data-ttu-id="babbf-134">Stisknutím klávesy F5 sestavte projekt a spusťte váš ovládací prvek **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="babbf-134">Press F5 to build the project and run your control in the **UserControl Test Container**.</span></span>  
  
2.  <span data-ttu-id="babbf-135">Najít `Strings` vlastnost <xref:System.Windows.Forms.PropertyGrid> z **UserControl – kontejner testů**.</span><span class="sxs-lookup"><span data-stu-id="babbf-135">Find the `Strings` property in the <xref:System.Windows.Forms.PropertyGrid> of the **UserControl Test Container**.</span></span> <span data-ttu-id="babbf-136">Klikněte na tlačítko `Strings` vlastnost, klepněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek obrazovky](../media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="babbf-136">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="babbf-137">Zadejte několik řetězců v **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="babbf-137">Enter several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="babbf-138">Oddělte je stisknutím klávesy ENTER na konci každého řetězce.</span><span class="sxs-lookup"><span data-stu-id="babbf-138">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="babbf-139">Klikněte na tlačítko **OK** po dokončení zadávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="babbf-139">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babbf-140">Zobrazí řetězce jste zadali v <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="babbf-140">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
## <a name="serializing-a-collection-property"></a><span data-ttu-id="babbf-141">Serializace vlastnost kolekce</span><span class="sxs-lookup"><span data-stu-id="babbf-141">Serializing a Collection Property</span></span>  
 <span data-ttu-id="babbf-142">K otestování chování serializace ovládacího prvku, umístěte ho na formuláři a změnit obsah kolekce s **Editor kolekce**.</span><span class="sxs-lookup"><span data-stu-id="babbf-142">To test the serialization behavior of your control, you will place it on a form and change the contents of the collection with the **Collection Editor**.</span></span> <span data-ttu-id="babbf-143">Zobrazí se stav serializovaná shromažďování zobrazením zvláštní soubor návrháře, do kterého **Návrháře formulářů Windows** emituje kód.</span><span class="sxs-lookup"><span data-stu-id="babbf-143">You can see the serialized collection state by looking at a special designer file, into which the **Windows Forms Designer** emits code.</span></span>  
  
#### <a name="to-serialize-a-collection"></a><span data-ttu-id="babbf-144">K serializaci kolekce</span><span class="sxs-lookup"><span data-stu-id="babbf-144">To serialize a collection</span></span>  
  
1.  <span data-ttu-id="babbf-145">Přidáte do řešení projekt aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="babbf-145">Add a Windows Application project to the solution.</span></span> <span data-ttu-id="babbf-146">Pojmenujte projekt `SerializationDemoControlTest`.</span><span class="sxs-lookup"><span data-stu-id="babbf-146">Name the project `SerializationDemoControlTest`.</span></span>  
  
2.  <span data-ttu-id="babbf-147">V **nástrojů**, najít na kartě s názvem **SerializationDemoControlLib komponenty**.</span><span class="sxs-lookup"><span data-stu-id="babbf-147">In the **Toolbox**, find the tab named **SerializationDemoControlLib Components**.</span></span> <span data-ttu-id="babbf-148">Na této kartě můžete najít `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="babbf-148">In this tab, you will find the `SerializationDemoControl`.</span></span> <span data-ttu-id="babbf-149">Další informace najdete v tématu [názorný postup: Automatické vyplnění nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span><span class="sxs-lookup"><span data-stu-id="babbf-149">For more information, see [Walkthrough: Automatically Populating the Toolbox with Custom Components](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).</span></span>  
  
3.  <span data-ttu-id="babbf-150">Místo `SerializationDemoControl` na formuláři.</span><span class="sxs-lookup"><span data-stu-id="babbf-150">Place a `SerializationDemoControl` on your form.</span></span>  
  
4.  <span data-ttu-id="babbf-151">Najít `Strings` vlastnost **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="babbf-151">Find the `Strings` property in the **Properties** window.</span></span> <span data-ttu-id="babbf-152">Klikněte na tlačítko `Strings` vlastnost, klepněte na tlačítko se třemi tečkami (![VisualStudioEllipsesButton snímek obrazovky](../media/vbellipsesbutton.png "vbEllipsesButton")) tlačítko Otevřít **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="babbf-152">Click the `Strings` property, then click the ellipsis (![VisualStudioEllipsesButton screenshot](../media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **String Collection Editor**.</span></span>  
  
5.  <span data-ttu-id="babbf-153">Zadejte několik řetězců v **Editor kolekce řetězců**.</span><span class="sxs-lookup"><span data-stu-id="babbf-153">Type several strings in the **String Collection Editor**.</span></span> <span data-ttu-id="babbf-154">Oddělte je stisknutím klávesy ENTER na konci každého řetězce.</span><span class="sxs-lookup"><span data-stu-id="babbf-154">Separate them by pressing the ENTER key at the end of each string.</span></span> <span data-ttu-id="babbf-155">Klikněte na tlačítko **OK** po dokončení zadávání řetězců.</span><span class="sxs-lookup"><span data-stu-id="babbf-155">Click **OK** when you are finished entering strings.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babbf-156">Zobrazí řetězce jste zadali v <xref:System.Windows.Forms.TextBox> z `SerializationDemoControl`.</span><span class="sxs-lookup"><span data-stu-id="babbf-156">The strings you typed appear in the <xref:System.Windows.Forms.TextBox> of the `SerializationDemoControl`.</span></span>  
  
1.  <span data-ttu-id="babbf-157">V **Průzkumníka řešení**, klikněte na tlačítko **zobrazit všechny soubory** tlačítko.</span><span class="sxs-lookup"><span data-stu-id="babbf-157">In **Solution Explorer**, click the **Show All Files** button.</span></span>  
  
2.  <span data-ttu-id="babbf-158">Otevřít **Form1** uzlu.</span><span class="sxs-lookup"><span data-stu-id="babbf-158">Open the **Form1** node.</span></span> <span data-ttu-id="babbf-159">Rat je soubor s názvem **Form1.Designer.cs** nebo **Form1.Designer.vb**.</span><span class="sxs-lookup"><span data-stu-id="babbf-159">Beneath it is a file called **Form1.Designer.cs** or **Form1.Designer.vb**.</span></span> <span data-ttu-id="babbf-160">Jedná se o soubor, do kterého **Návrháře formulářů Windows** emituje kód představující stav návrhu a jeho podřízených ovládacích prvků formuláře.</span><span class="sxs-lookup"><span data-stu-id="babbf-160">This is the file into which the **Windows Forms Designer** emits code representing the design-time state of your form and its child controls.</span></span> <span data-ttu-id="babbf-161">Tento soubor otevřít v **Editor kódu**.</span><span class="sxs-lookup"><span data-stu-id="babbf-161">Open this file in the **Code Editor**.</span></span>  
  
3.  <span data-ttu-id="babbf-162">Otevřete oblast volá **kód generovaný návrhářem formulářů Windows** a vyhledejte část s názvem **serializationDemoControl1**.</span><span class="sxs-lookup"><span data-stu-id="babbf-162">Open the region called **Windows Form Designer generated code** and find the section labeled **serializationDemoControl1**.</span></span> <span data-ttu-id="babbf-163">Pod tento popisek je kód představující serializovaný stav ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="babbf-163">Beneath this label is the code representing the serialized state of your control.</span></span> <span data-ttu-id="babbf-164">Řetězce, které jste zadali v kroku 5 jsou zobrazeny v přiřazení k `Strings` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="babbf-164">The strings you typed in step 5 appear in an assignment to the `Strings` property.</span></span> <span data-ttu-id="babbf-165">Následující příklady kódu v C# a Visual Basic, zobrazit kód podobný co se zobrazí pokud jste zadali řetězce "red", "oranžové" a "žlutý".</span><span class="sxs-lookup"><span data-stu-id="babbf-165">The following code examples in C# and Visual Basic, show code similar to what you will see if you typed the strings "red", "orange", and "yellow".</span></span>  
  
    ```csharp  
    this.serializationDemoControl1.Strings = new string[] {  
            "red",  
            "orange",  
            "yellow"};  
    ```  
    
    ```vb  
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}  
    ```
  
4.  <span data-ttu-id="babbf-166">V **Editor kódu**, změňte hodnotu <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> na `Strings` vlastnost <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span><span class="sxs-lookup"><span data-stu-id="babbf-166">In the **Code Editor**, change the value of the <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> on the `Strings` property to <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>.</span></span>  
  
    ```csharp  
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]  
    ```  
    ```vb  
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _  
    ```  
  
5. <span data-ttu-id="babbf-167">Znovu sestavte řešení a zopakujte kroky 3 a 4.</span><span class="sxs-lookup"><span data-stu-id="babbf-167">Rebuild the solution and repeat steps 3 and 4.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="babbf-168">V takovém případě **Návrháře formulářů Windows** vysílá žádné přiřazení `Strings` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="babbf-168">In this case, the **Windows Forms Designer** emits no assignment to the `Strings` property.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="babbf-169">Další kroky</span><span class="sxs-lookup"><span data-stu-id="babbf-169">Next Steps</span></span>  
 <span data-ttu-id="babbf-170">Když víte, jak serializace kolekcí standardních typů, vezměte v úvahu integrace vlastních ovládacích prvků hlouběji do návrhové prostředí.</span><span class="sxs-lookup"><span data-stu-id="babbf-170">Once you know how to serialize a collection of standard types, consider integrating your custom controls more deeply into the design-time environment.</span></span> <span data-ttu-id="babbf-171">Následující témata popisují, jak vylepšit návrhu integrace vlastních ovládacích prvků:</span><span class="sxs-lookup"><span data-stu-id="babbf-171">The following topics describe how to enhance the design-time integration of your custom controls:</span></span>  
  
-   [<span data-ttu-id="babbf-172">Architektura návrhu</span><span class="sxs-lookup"><span data-stu-id="babbf-172">Design-Time Architecture</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))  
  
-   [<span data-ttu-id="babbf-173">Atributy v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="babbf-173">Attributes in Windows Forms Controls</span></span>](attributes-in-windows-forms-controls.md)  
  
-   [<span data-ttu-id="babbf-174">Přehled serializace návrháře</span><span class="sxs-lookup"><span data-stu-id="babbf-174">Designer Serialization Overview</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))  
  
-   [<span data-ttu-id="babbf-175">Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu</span><span class="sxs-lookup"><span data-stu-id="babbf-175">Walkthrough: Creating a Windows Forms Control That Takes Advantage of Visual Studio Design-Time Features</span></span>](creating-a-wf-control-design-time-features.md)  
  
## <a name="see-also"></a><span data-ttu-id="babbf-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="babbf-176">See also</span></span>

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [<span data-ttu-id="babbf-177">Přehled serializace návrháře</span><span class="sxs-lookup"><span data-stu-id="babbf-177">Designer Serialization Overview</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))
- [<span data-ttu-id="babbf-178">Postupy: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute</span><span class="sxs-lookup"><span data-stu-id="babbf-178">How to: Serialize Collections of Standard Types with the DesignerSerializationVisibilityAttribute</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120))
- [<span data-ttu-id="babbf-179">Návod: Automatické vyplnění sady nástrojů vlastními komponentami</span><span class="sxs-lookup"><span data-stu-id="babbf-179">Walkthrough: Automatically Populating the Toolbox with Custom Components</span></span>](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
