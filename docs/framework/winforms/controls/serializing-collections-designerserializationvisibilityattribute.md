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
ms.openlocfilehash: 4fd1f1dc0c2c0ad9ae2009ed592e48b8eeaa2783
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373677"
---
# <a name="walkthrough-serialize-collections-of-standard-types"></a>Návod: Serializace kolekcí standardních typů

Vaše vlastní ovládací prvky budou někdy vystavovat kolekci jako vlastnost. Tento návod ukazuje, jak použít <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> třídu pro řízení způsobu serializace kolekce v době návrhu. <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Použití hodnoty na vlastnost kolekce zajistí, že bude vlastnost serializována.

Postup kopírování kódu v tomto tématu jako jediného výpisu naleznete v [tématu How to: Serializace kolekcí standardních typů s DesignerSerializationVisibilityAttribute](/previous-versions/visualstudio/visual-studio-2013/ms171833(v=vs.120)).

## <a name="prerequisites"></a>Požadavky

K dokončení tohoto Názorného postupu potřebujete Visual Studio.

## <a name="create-a-control-with-a-serializable-collection"></a>Vytvoření ovládacího prvku s serializovatelný kolekcí

Prvním krokem je vytvoření ovládacího prvku, který má serializovatelné kolekce jako vlastnost. Obsah této kolekce můžete upravit pomocí **editoru kolekce**, ke kterému můžete přistupovat z okna **vlastnosti** .

1. V aplikaci Visual Studio vytvořte projekt knihovny ovládacích prvků systému Windows a pojmenujte jej **SerializationDemoControlLib**.

2. Přejmenujte `UserControl1` na `SerializationDemoControl`. Další informace najdete v tématu [přejmenování refaktoringu symbolů kódu](/visualstudio/ide/reference/rename).

3. V okně **vlastnosti** nastavte hodnotu <xref:System.Windows.Forms.Padding.All%2A?displayProperty=nameWithType> vlastnosti na hodnotu **10**.

4. Umístěte ovládací prvek do `SerializationDemoControl`. <xref:System.Windows.Forms.TextBox>

5. <xref:System.Windows.Forms.TextBox> Vyberte ovládací prvek. V okně **vlastnosti** nastavte následující vlastnosti.

    |Vlastnost|Změnit na|
    |--------------|---------------|
    |**Víceřádkový**|`true`|
    |**Vyjměte**|<xref:System.Windows.Forms.DockStyle.Fill>|
    |**Posuvníky**|<xref:System.Windows.Forms.ScrollBars.Vertical>|
    |**ReadOnly**|`true`|

6. V **editoru kódu**deklarujte pole řetězců s názvem `stringsValue` v. `SerializationDemoControl`

     [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#4)]
     [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#4)]
     [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#4)]

7. `Strings` Definujte vlastnost`SerializationDemoControl`na.

   > [!NOTE]
   > <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute.Content> Hodnota se používá k povolení serializace kolekce.

   [!code-cpp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/cpp/form1.cpp#5)]
   [!code-csharp[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/CS/form1.cs#5)]
   [!code-vb[System.ComponentModel.DesignerSerializationVisibilityAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.DesignerSerializationVisibilityAttribute/VB/form1.vb#5)]

8. Stisknutím klávesy **F5** Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.

9. V<xref:System.Windows.Forms.PropertyGrid> **kontejneru testu UserControl**vyhledejte vlastnost Strings. Vyberte vlastnost **řetězce** a potom vyberte tři tečky (![tři tečky (...) v okno Vlastnosti sadě Visual Studio](./media/visual-studio-ellipsis-button.png)) a otevřete **Editor kolekce řetězců**.

10. V **editoru kolekce řetězců**zadejte několik řetězců. Oddělte je stisknutím klávesy **ENTER** na konci každého řetězce. Po dokončení zadávání řetězců klikněte na **OK** .

   > [!NOTE]
   > Řetězce, které jste zadali, se <xref:System.Windows.Forms.TextBox> zobrazí v `SerializationDemoControl`části.

## <a name="serialize-a-collection-property"></a>Serializace vlastnosti kolekce

Chcete-li otestovat chování serializace ovládacího prvku, umístěte ho do formuláře a změňte obsah kolekce pomocí **editoru kolekce**. Serializovaný stav shromažďování můžete zobrazit tak, že prohlížíte speciální soubor návrháře, do kterého **Návrhář formulářů** generuje kód.

1. Přidejte do řešení projekt aplikace pro Windows. Pojmenujte `SerializationDemoControlTest`projekt.

2. V **sadě nástrojů**Najděte kartu s názvem **součásti SerializationDemoControlLib**. Na této kartě najdete `SerializationDemoControl`. Další informace najdete v tématu [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md).

3. Umístěte objekt `SerializationDemoControl` do formuláře.

4. V okně **vlastnosti** vyhledejte vlastnost.`Strings` Klikněte na![](./media/visual-studio-ellipsis-button.png)vlastnost a potom kliknutím na tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio.) otevřete **Editor kolekce řetězců.** `Strings`

5. Zadejte několik řetězců v **editoru kolekce řetězců**. Oddělte je stisknutím klávesy **ENTER** na konci každého řetězce. Po dokončení zadávání řetězců klikněte na **OK** .

    > [!NOTE]
    > Řetězce, které jste zadali, se <xref:System.Windows.Forms.TextBox> zobrazí v `SerializationDemoControl`části.

6. V **Průzkumník řešení**klikněte na tlačítko **Zobrazit všechny soubory** .

7. Otevřete uzel **Form1** . Pod ním je soubor s názvem **Form1.Designer.cs** nebo **Form1. Designer. vb**. Jedná se o soubor, do kterého **Návrhář formulářů** emituje kód, který představuje stav při návrhu formuláře a jeho podřízených ovládacích prvků. Otevřete tento soubor v **editoru kódu**.

8. Otevřete oblast nazvanou **Windows Form Designer generovaný kód** a najděte oddíl označený **serializationDemoControl1**. Pod tímto popiskem je kód představující serializovaný stav vašeho ovládacího prvku. Řetězce, které jste zadali v kroku 5, se zobrazí v přiřazení `Strings` k vlastnosti. Následující příklady kódu v C# a Visual Basic ukazují kód podobný tomu, co se vám zobrazí, pokud jste zadali řetězce "Red", "oranžová" a "žlutá".

    ```csharp
    this.serializationDemoControl1.Strings = new string[] {
            "red",
            "orange",
            "yellow"};
    ```

    ```vb
    Me.serializationDemoControl1.Strings = New String() {"red", "orange", "yellow"}
    ```

9. V **editoru kódu**změňte hodnotu <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute> `Strings` vlastnosti <xref:System.ComponentModel.DesignerSerializationVisibility.Hidden>na.

    ```csharp
    [DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)]
    ```

    ```vb
    <DesignerSerializationVisibility(DesignerSerializationVisibility.Hidden)> _
    ```

10. Znovu sestavte řešení a opakujte kroky 3 a 4.

> [!NOTE]
> V takovém případě **Návrhář formulářů** negeneruje žádné přiřazení k `Strings` vlastnosti.

## <a name="next-steps"></a>Další postup

Jakmile se dozvíte, jak serializovat kolekci standardních typů, zvažte integraci vlastních ovládacích prvků do prostředí v době návrhu. Následující témata popisují, jak vylepšit integraci vlastních ovládacích prvků v době návrhu:

- [Architektura v době návrhu](/previous-versions/visualstudio/visual-studio-2013/c5z9s1h4(v=vs.120))

- [Atributy v ovládacích prvcích Windows Forms](attributes-in-windows-forms-controls.md)

- [Přehled serializace návrháře](/previous-versions/visualstudio/visual-studio-2013/ms171834(v=vs.120))

- [Návod: Vytvoření ovládacího prvku model Windows Forms, který využívá výhod funkcí nástroje Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md)

## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.DesignerSerializationVisibilityAttribute>
- [Návod: Automatické vyplnění sady nástrojů vlastními komponentami](walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
