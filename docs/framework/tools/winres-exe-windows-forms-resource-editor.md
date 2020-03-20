---
title: Winres.exe (Editor lokalizace prostředků systému Windows)
ms.date: 08/15/2018
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- Windows Resource Localization Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
ms.openlocfilehash: 2cfb2d9874b34eef78fe462e0270fd70307a9f61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715706"
---
# <a name="winresexe-windows-resource-localization-editor"></a>Winres.exe (Editor lokalizace prostředků systému Windows)

Editor lokalizace prostředků systému Windows Winres.exe je nástroj pro vizuální rozložení, který pomáhá odborníkům na lokalizaci lokalizovat prostředky uživatelského rozhraní (UI) windows forms používané formuláři. Soubor prostředků .resx nebo .resources sloužící jako vstup do nástroje Winres.exe lze vytvořit pomocí prostředí pro vizuální návrh, jako je například sada Microsoft Visual Studio. Informace o nasazení prostředků v aplikacích rozhraní .NET Framework naleznete [v tématu Resources in Desktop Apps](../resources/index.md).

Program Winres.exe je nainstalován v sadě Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio. Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

## <a name="syntax"></a>Syntaxe

```console
winres resourceFile
winres /?
```

## <a name="arguments"></a>Argumenty

|Argument|Popis|
|--------------|-----------------|
|`resourceFile`|Soubor prostředků k lokalizaci. Tento soubor musí být formulář Windows Forms s příponou .resx nebo .resources vygenerovaný pomocí návrháře sady Visual Studio. Nástroj Winres.exe nedokáže otevřít obecné soubory .resx nebo .resources.|

|Možnost|Popis|
|------------|-----------------|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

## <a name="remarks"></a>Poznámky

Stavy prvků UI z formuláře v projektu Windows Forms jsou obvykle uloženy v souborech prostředků s příponou .resx založených na XML nebo v souborech odpovídajících zkompilovaných binárních verzí s příponou .resources. Winres.exe je nástroj umožňující omezené úpravy obou typů souborů mimo návrhové prostředí sady Visual Studio. Konkrétně umožňuje následující typy operací úprav:

- Chcete-li změnit vlastnosti uživatelského rozhraní (UI) formuláře, můžete upravit soubor prostředků neutrální nebo konkrétní jazykové verze nebo jeho ovládací prvky jako například text, velikost či umístění.

- Soubory prostředků neutrální nebo konkrétní jazykové verze mohou být generovány z výchozího souboru prostředků.

- Soubor prostředků jazykové verze lze uložit jako soubor prostředků jiné jazykové verze. Například soubor prostředků pro angličtinu (USA) může být uložen jako soubor prostředků pro polštinu. Nový soubor bude obvykle upraven tak, aby byl kompatibilní s novou jazykovou verzí.

Viz také [hierarchická organizace prostředků pro lokalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/756hydy4(v=vs.110)) nebo [hierarchická organizace prostředků pro lokalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/756hydy4(v=vs.120)).

Nástroj Winres.exe nemůže převést soubor .resx na dopovídající soubor .resources; použijte místo něj nástroj Resgen.exe. Další informace o resgen.exe naleznete [v tématu Resgen.exe (Resource File Generator)](resgen-exe-resource-file-generator.md).

Nástroj Winres.exe je grafická aplikace, která obnoví verzi návrhu formuláře Windows Forms pouze ze souboru prostředků, aniž by měla přístup ke zdrojovému kódu. Program Winres.exe hostuje okno Návrháře formulářů a **vlastností** **formulářů systému Windows** sady Visual Studio. Tyto funkce umožňují provádět vizuální úpravy souboru .resources nebo .resx obsahujícího formulář Windows Forms. Lokalizátory obvykle používají winres.exe k úpravě popisků ovládacích prvků a úpravě umístění a velikosti ovládacích prvků tak, aby odpovídaly popisky pro cílovou jazykovou verzi.

Pokud nástroj Winres.exe nedokáže rozlišit verzi ovládacího prvku, vytvoří v lokalizovaném souboru .resx nebo .resources zástupný text ovládacího prvku. Zástupný text ovládacího prvku se zobrazí ve formuláři Windows Forms jako šrafované okno. Velikost a umístění šrafovaného okna odpovídá skutečnému ovládacímu prvku. Všechny dostupné lokalizovatelné vlastnosti zástupného ovládacího prvku se zobrazí v okně **Vlastnosti.** Veškeré změny provedené v zástupném textu ovládacího prvku se uloží pro skutečný ovládací prvek.

## <a name="winresexe-versus-visual-studio"></a>Srovnání nástroje Winres.exe a sady Visual Studio

Obecně platí, že dříve než začnete lokalizovat formuláře Windows Forms pro určitou aplikaci, měli byste se rozhodnout, zda chcete k lokalizaci použít sadu Visual Studio, nebo nástroj Winres.exe. Kompatibilita verzí, jak je popsáno dále, může bránit přepínání z jednoho nástroje na druhý.

Výhodou sady Visual Studio je, že ji můžete použít k vývoji i lokalizaci aplikace. Chcete-li lokalizovat formulář, po dokončení vývoje <xref:System.ComponentModel.LocalizableAttribute> nastavte formulář **(lokalizovatelné vlastnosti** `true` v editoru **vlastnosti)** a změnit jeho **Language** vlastnost požadovanou cílovou jazykovou verzi. Poté změňte řetězce a upravte umístění a velikost ovládacích prvků tak, aby vyhovovaly řetězcům cílové jazykové verze. Při ukládání lokalizovaného souboru .resx sada Visual Studio do souboru zapíše pouze lokalizovatelné vlastnosti (vlastnosti, které se v cílové jazykové verzi změnily). Sada Visual Studio automaticky vytvoří satelitní sestavení pro lokalizovaný soubor .resx ve správném adresáři.

Přestože Visual Studio poskytuje integrované vývojové a lokalizační prostředí, winres.exe je doporučený nástroj pro použití, pokud lokalizace se provádí lokalizátory jiných výrobců. Protože Winres.exe je pouze lokalizační nástroj, umožňuje jasnější oddělení kódu aplikace od formulářů určených k lokalizaci, což je při řízení velkých projektů praktičtější.

## <a name="using-winresexe"></a>Používání nástroje Winres.exe

Chcete-li lokalizovat pomocí programu Winres.exe, musíte nejprve vyvinout aplikaci pomocí vizuálního návrháře, jako je **Návrhář formulářů Systému Windows** v sadě Visual Studio. Po dokončení vývoje nastavte formulář <xref:System.ComponentModel.LocalizableAttribute> **(lokalizovatelné vlastnosti** v editoru `true` **vlastnosti)** na , a pak předat soubor .resx pro výchozí jazykovou verzi lokalizátoru jiného výrobce. Tento soubor .resx obsahuje další informace, které nástroj Winres.exe použije k obnovení verze návrhu původního formuláře.

> [!NOTE]
> Nástroj Winres.exe nelze použít k úpravě výchozího souboru prostředků. Nástroj Winres.exe interpretuje všechny změněné vlastnosti jako lokalizované vlastnosti a ukládá je do souboru prostředků cílové jazykové verze.

Konečné verze souborů prostředků jazykové verze lze nakonec použít k vytvoření lokalizovaných verzí aplikace. Další informace naleznete [v tématu Resources in Desktop Apps](../resources/index.md).

Winres.exe má následující funkce a možnosti:

- Nástroj Winres může pracovat v režimu Single File Mode (SFM) nebo v režimu Visual Studio File Mode (VSFM). SFM je starší režim, ve kterém jsou úplné informace o formuláři a jeho obsahu uloženy do souboru prostředků. Režim VSFM ukládá pouze změny jazykové verze v souboru prostředků.

- Okno hlášení chyb ukotvené k levému dolnímu rohu hlavního okna.

- Klávesové zkratky lze zkontrolovat, zda neobsahuje duplicity: v nabídce **Formát** klepněte na příkaz **Zkontrolovat klávesové zkratky.**

## <a name="version-compatibility"></a>Kompatibilita verzí

Měli byste použít verzi programu Winres.exe, která byla vydána s rozhraním .NET Framework, který používáte. V následující tabulce jsou uvedeny kompatibilní verze:

|Visual Studio|.NET Framework|Winres.exe|
|-------------------|--------------------|----------------|
|Visual Studio .NET 2002|1.0|1.0|
|Visual Studio .NET 2003|1.1|1.1|
|Visual Studio 2005|2.0|2.0|
|Visual Studio 2008|3.0 a 3.5|3.0 a 3.5|
|Visual Studio 2010|4.0|4.0|
|Visual Studio 2017|4.6|4.6|

> [!NOTE]
> Ačkoli se režim VSFM vyznačuje výhodou kompatibility se sadou Visual Studio, tak vzhledem k tomu, že do souboru prostředků jsou uloženy pouze změněné hodnoty, nástroj Winres.exe vyžaduje, aby se soubory nadřazené aktuálnímu souboru prostředků nacházely ve stejném adresáři. Například úpravy `TestApp.de-DE.resources`, německý soubor prostředků v Německu, vyžaduje přítomnost `TestApp.resx`výchozího souboru prostředků a `TestApp.de.resources`případně soubor prostředků neutrální z jazykové verze .

## <a name="examples"></a>Příklady

### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Lokalizace souborů .resx nebo .resources spojených s formulářem

1. Chcete-li spustit soubor Winres.exe, zadejte `winres` příkazový řádek vývojáře.

2. Chcete-li otevřít výchozí prostředky pro lokalizaci formuláře, klepněte na příkaz **Otevřít** v nabídce **Soubor** a přejděte na soubor a otevřete jej.

     -nebo-

     Při spouštění nástroje Winres.exe do příkazového řádku zadejte název otevíraného souboru.

     Následující příkaz spustí soubor Winres.exe a `TestApp.resx` načte formulář přidružený k návrháři formulářů.

    ```console
    winres TestApp.resx
    ```

     Následující příkaz spustí soubor Winres.exe a `TestApp.resources` načte formulář přidružený k návrháři formulářů.

    ```console
    winres TestApp.resources
    ```

    > [!NOTE]
    > Jestliže je formulář, jehož prostředky upravujete, zděděným formulářem, sestavení obsahující zděděný formulář i sestavení obsahující odvozený formulář musí být zaregistrována v globální mezipaměti sestavení (GAC) nebo musí být umístěna ve stejném adresáři jako nástroj WinRes.exe. Další informace o instalaci součástí rozhraní .NET Framework do gac naleznete v [tématu Global Assembly Cache](../app-domains/gac.md).

3. Vyberte ovládací prvky <xref:System.Windows.Forms.Control.Text%2A> ve formuláři a změňte jejich a další vlastnosti tak, aby odrážely lokalizovanou jazykovou verzi a její jazyk. Přesuňte ovládací prvky nebo změňte jejich velikost tak, aby vyhovovaly lokalizovanému textu.

4. Chcete-li uložit lokalizovanou verzi souboru Resx nebo .resources, klepněte v nabídce **Soubor** na ikonu **Uložit** nebo stejný příkaz. Nástroj zobrazí okno **Vybrat jazykovou verzi.**

5. Vyberte příslušnou jazykovou verzi a režim souboru a klepněte na tlačítko **OK**.

   Nástroj uloží soubor pomocí konvence pojmenování, kterou čas spuštění očekává pro lokalizované soubory prostředků. Pokud například lokalizujete `TestApp.resources` pro němčinu v Německu, `TestApp.de-DE.resources`nástroj uloží soubor jako . Pokud lokalizujete `TestApp.resx` pro němčinu v Německu, `TestApp.de-DE.resx`nástroj uloží soubor jako . Další informace o konvencích pojmenování prostředků naleznete [v tématu Balení a nasazení prostředků](../resources/packaging-and-deploying-resources-in-desktop-apps.md). Seznam předdefinovaných názvů kultur používaných časem běhu <xref:System.Globalization.CultureInfo> naleznete ve třídě.

## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.LocalizableAttribute>
- <xref:System.Globalization.CultureInfo>
- <xref:System.Resources.ResourceManager>
- <xref:System.Resources.ResourceReader>
- <xref:System.Resources.ResourceWriter>
- [Nástroje](index.md)
- [Prostředky v aplikacích klasické pracovní plochy](../resources/index.md)
- [Globalizace a lokalizace](../../standard/globalization-localization/index.md)
