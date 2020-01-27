---
title: Ladit vlastní ovládací prvky v době návrhu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- custom controls [Windows Forms], walkthroughs
- visual editors
- debugging [Visual Studio], Windows Forms
- custom controls [Windows Forms], debugging
- designers
- controls [Windows Forms], debugging
- walkthroughs [Windows Forms], debugging
- design-time debugging
ms.assetid: 1fd83ccd-3798-42fc-85a3-6cba99467387
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9e292a1219c24571bcb35db2fe357b0197c8812
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740195"
---
# <a name="walkthrough-debug-custom-windows-forms-controls-at-design-time"></a>Návod: ladění vlastních ovládacích prvků model Windows Forms v době návrhu

Při vytváření vlastního ovládacího prvku často zjistíte, že je nutné ladit jeho chování při návrhu. To platí hlavně v případě, že vytváříte vlastního návrháře vlastního ovládacího prvku. Podrobnosti najdete v tématu [Návod: vytváření model Windows Forms ovládacího prvku, který využívá výhod funkcí Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md).

Pomocí sady Visual Studio můžete ladit vlastní ovládací prvky stejně, jako byste provedete ladění jakékoli jiné .NET Framework třídy. Rozdíl je, že budete ladit samostatnou instanci aplikace Visual Studio, která spouští kód vlastního ovládacího prvku.

## <a name="create-the-project"></a>Vytvoření projektu

Prvním krokem je vytvoření projektu aplikace. Pomocí tohoto projektu sestavíte aplikaci, která je hostitelem vlastního ovládacího prvku.

V aplikaci Visual Studio vytvořte projekt aplikace pro systém Windows a pojmenujte jej **DebuggingExample**.

## <a name="create-the-control-library-project"></a>Vytvořit projekt knihovny ovládacích prvků

1. Přidejte do řešení projekt **knihovny ovládacích prvků systému Windows** .

2. Přidejte novou položku **UserControl** do projektu DebugControlLibrary. Pojmenujte ho **DebugControl**.

3. V **Průzkumník řešení**odstraňte výchozí ovládací prvek projektu odstraněním souboru s kódem se základním názvem UserControl1.

4. Sestavte řešení.

## <a name="checkpoint"></a>CheckPoint

V tomto okamžiku budete moci zobrazit vlastní ovládací prvek v sadě **nástrojů**.

Pokud chcete zjistit svůj průběh, najděte novou kartu s názvem **součásti DebugControlLibrary** a kliknutím ji vyberte. Po otevření se ovládací prvek zobrazí jako **DebugControl** s výchozí ikonou vedle něj.

## <a name="add-a-property-to-your-custom-control"></a>Přidání vlastnosti do vlastního ovládacího prvku

Chcete-li předvést, že váš kód vlastního ovládacího prvku je spuštěn v době návrhu, přidejte vlastnost a nastavte zarážku v kódu, který implementuje vlastnost.

1. Otevřete **DebugControl** v **editoru kódu**. Do definice třídy přidejte následující kód:

    ```vb
    Private demoStringValue As String = Nothing
    <BrowsableAttribute(true)>
    Public Property DemoString() As String

        Get
            Return Me.demoStringValue
        End Get

        Set(ByVal value As String)
            Me.demoStringValue = value
        End Set

    End Property
    ```

    ```csharp
    private string demoStringValue = null;
    [Browsable(true)]
    public string DemoString
    {
        get
        {
            return this.demoStringValue;
        }
        set
        {
            demoStringValue = value;
        }
    }
    ```

2. Sestavte řešení.

## <a name="add-your-custom-control-to-the-host-form"></a>Přidat vlastní ovládací prvek do formuláře hostitele

Chcete-li ladit chování vlastního ovládacího prvku v době návrhu, umístěte instanci třídy vlastního ovládacího prvku do formuláře hostitele.

1. V projektu "DebuggingExample" otevřete Form1 v **Návrhář formulářů**.

2. V **sadě nástrojů**otevřete kartu **součásti DebugControlLibrary** a přetáhněte instanci **DebugControl** do formuláře.

3. V okně **vlastnosti** vyhledejte vlastní vlastnost `DemoString`. Všimněte si, že můžete změnit její hodnotu stejně jako jakoukoli jinou vlastnost. Všimněte si také, že pokud je vybrána vlastnost `DemoString`, zobrazí se v dolní části okna **vlastností** řetězec popisu vlastnosti.

## <a name="set-up-the-project-for-design-time-debugging"></a>Nastavení projektu pro ladění v době návrhu

Chcete-li ladit chování vlastního ovládacího prvku v době návrhu, budete ladit samostatnou instanci aplikace Visual Studio, ve které je spuštěn kód vlastního ovládacího prvku.

1. V **Průzkumník řešení** klikněte pravým tlačítkem na projekt **DebugControlLibrary** a vyberte **vlastnosti**.

2. V seznamu vlastností **DebugControlLibrary** vyberte kartu **ladění** .

     V části **spouštěcí akce** vyberte **spustit externí program**. Budete ladit samostatnou instanci aplikace Visual Studio, proto klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual Studio](./media/visual-studio-ellipsis-button.png)) a vyhledejte integrované vývojové prostředí (IDE) sady Visual Studio. Název spustitelného souboru je **devenv. exe**a pokud jste nainstalovali do výchozího umístění, jeho cesta je *% ProgramFiles (x86)% \ Microsoft Visual Studio\2019\\\<Edition > \Common7\IDE*.

3. Kliknutím na **tlačítko OK** zavřete dialogové okno.

4. Klikněte pravým tlačítkem na projekt **DebugControlLibrary** a vyberte **nastavit jako spouštěný projekt** , abyste mohli tuto konfiguraci ladění povolit.

## <a name="debug-your-custom-control-at-design-time"></a>Ladění vlastního ovládacího prvku v době návrhu

Nyní jste připraveni ladit vlastní ovládací prvek při spuštění v režimu návrhu. Když spustíte relaci ladění, vytvoří se nová instance aplikace Visual Studio, kterou použijete k načtení řešení "DebuggingExample". Když otevřete Form1 v **Návrháři formulářů**, vytvoří se instance vlastního ovládacího prvku a spustí se.

1. Otevřete zdrojový soubor **DebugControl** v **editoru kódu** a umístěte zarážku na přistupující objekt `Set` vlastnosti `DemoString`.

2. Stisknutím klávesy **F5** spusťte relaci ladění. Vytvoří se nová instance sady Visual Studio. Mezi instancemi můžete rozlišovat dvěma způsoby:

    - Instance ladění má slovo **běžící** v záhlaví.

    - Instance ladění má tlačítko **Spustit** na panelu nástrojů **ladění** zakázáno.

   Zarážka je nastavena v instanci ladění.

3. V nové instanci aplikace Visual Studio otevřete řešení "DebuggingExample". Řešení můžete snadno najít výběrem položky **Poslední projekty** v nabídce **soubor** . Soubor řešení "DebuggingExample. sln" bude uveden jako naposledy použitý soubor.

4. Otevřete Form1 v **Návrháři formulářů** a vyberte ovládací prvek **DebugControl** .

5. Změňte hodnotu vlastnosti `DemoString`. Když změníte změnu, instance ladění sady Visual Studio získá fokus a spuštění se zastaví na zarážce. Přístup k jednotlivým krokům můžete procházet prostřednictvím přistupujícího objektu vlastnosti stejně jako jakýkoli jiný kód.

6. Chcete-li zastavit ladění, ukončete hostovanou instanci sady Visual Studio nebo vyberte tlačítko **Zastavit ladění** v instanci ladění.

## <a name="next-steps"></a>Další kroky

Nyní, když můžete ladit vlastní ovládací prvky v době návrhu, existuje mnoho možností pro rozšíření interakce ovládacího prvku pomocí integrovaného vývojového prostředí (IDE) sady Visual Studio.

- Můžete použít vlastnost <xref:System.ComponentModel.Component.DesignMode%2A> třídy <xref:System.ComponentModel.Component> k zápisu kódu, který bude proveden pouze v době návrhu. Podrobnosti najdete v tématu <xref:System.ComponentModel.Component.DesignMode%2A>.

- Existuje několik atributů, které lze použít pro vlastnosti ovládacího prvku pro manipulaci s interakcí vlastního ovládacího prvku s návrhářem. Tyto atributy můžete najít v oboru názvů <xref:System.ComponentModel?displayProperty=nameWithType>.

- Můžete napsat vlastní Návrhář pro vlastní ovládací prvek. Díky tomu máte plnou kontrolu nad prostředím pro návrh pomocí rozšiřitelné infrastruktury návrháře zveřejněné v rámci sady Visual Studio. Podrobnosti najdete v tématu [Návod: vytváření model Windows Forms ovládacího prvku, který využívá výhod funkcí Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md).

## <a name="see-also"></a>Viz také:

- [Návod: Vytvoření ovládacího prvku Windows Forms, který využívá funkce sady Visual Studio pro dobu návrhu](creating-a-wf-control-design-time-features.md)
