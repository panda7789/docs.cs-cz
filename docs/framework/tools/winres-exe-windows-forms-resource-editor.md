---
title: Winres.exe (Editor lokalizace prostředků Windows)
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5b9cb36c3ab7096e048905e56136f0de62a65bdc
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221092"
---
# <a name="winresexe-windows-resource-localization-editor"></a>Winres.exe (Editor lokalizace prostředků Windows)

Lokalizace Editor prostředků Windows, Winres.exe je nástroj rozložení vizuálu, který pomáhá odborníkům přes lokalizaci lokalizovat prostředky uživatelského rozhraní (UI) Windows Forms používané formuláři. Soubor prostředků .resx nebo .resources sloužící jako vstup do nástroje Winres.exe lze vytvořit pomocí prostředí pro vizuální návrh, jako je například sada Microsoft Visual Studio. Informace o nasazení prostředků v aplikacích .NET Framework najdete v tématu [prostředky v desktopových aplikací](../../../docs/framework/resources/index.md).

Winres.exe je instalace sady Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro sadu Visual Studio. Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

## <a name="syntax"></a>Syntaxe

```
winres resourceFile
winres /?
```

## <a name="arguments"></a>Arguments

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

Viz také [hierarchická organizace zdrojů pro lokalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2012/756hydy4(v=vs.110)) nebo [hierarchická organizace zdrojů pro lokalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/756hydy4(v=vs.120)).

Nástroj Winres.exe nemůže převést soubor .resx na dopovídající soubor .resources; použijte místo něj nástroj Resgen.exe. Další informace o Resgen.exe najdete v tématu [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

Nástroj Winres.exe je grafická aplikace, která obnoví verzi návrhu formuláře Windows Forms pouze ze souboru prostředků, aniž by měla přístup ke zdrojovému kódu. Winres.exe je hostitelem aplikace Visual Studio **Windows Forms Form Designer** a **vlastnosti** okna. Tyto funkce umožňují provádět vizuální úpravy souboru .resources nebo .resx obsahujícího formulář Windows Forms. Lokalizátoři obvykle používají Winres.exe k úpravě popisků ovládacích prvků a upravte umístění a velikosti ovládacích prvků tak, aby vyhovovaly popisků cílové jazykové verze.

Pokud nástroj Winres.exe nedokáže rozlišit verzi ovládacího prvku, vytvoří v lokalizovaném souboru .resx nebo .resources zástupný text ovládacího prvku. Zástupný text ovládacího prvku se zobrazí ve formuláři Windows Forms jako šrafované okno. Velikost a umístění šrafovaného okna odpovídá skutečnému ovládacímu prvku. Zobrazí všechny dostupné lokalizovatelné vlastnosti ovládacího prvku zástupného prvku v **vlastnosti** okna. Veškeré změny provedené v zástupném textu ovládacího prvku se uloží pro skutečný ovládací prvek.

## <a name="winresexe-versus-visual-studio"></a>Srovnání nástroje Winres.exe a sady Visual Studio

Obecně platí, že dříve než začnete lokalizovat formuláře Windows Forms pro určitou aplikaci, měli byste se rozhodnout, zda chcete k lokalizaci použít sadu Visual Studio, nebo nástroj Winres.exe. Kompatibilita verzí, jak je popsáno dále, může bránit přepínání z jednoho nástroje na druhý.

Výhodou sady Visual Studio je, že ji můžete použít k vývoji i lokalizaci aplikace. Po dokončení vývoje lokalizovat formulář, nastavte <xref:System.ComponentModel.LocalizableAttribute> ( **Localizable** vlastnost **vlastnosti** editoru) k `true` a změňte jeho  **Jazyk** vlastnost na požadovanou cílovou jazykovou verzi. Poté změňte řetězce a upravte umístění a velikost ovládacích prvků tak, aby vyhovovaly řetězcům cílové jazykové verze. Při ukládání lokalizovaného souboru .resx sada Visual Studio do souboru zapíše pouze lokalizovatelné vlastnosti (vlastnosti, které se v cílové jazykové verzi změnily). Sada Visual Studio automaticky vytvoří satelitní sestavení pro lokalizovaný soubor .resx ve správném adresáři.

Přestože Visual Studio poskytuje integrované vývojové a lokalizační prostředí, Winres.exe je doporučeným nástrojem k použijte, pokud lokalizace provádí Lokalizátoři třetích stran. Protože Winres.exe je pouze lokalizační nástroj, umožňuje jasnější oddělení kódu aplikace od formulářů určených k lokalizaci, což je při řízení velkých projektů praktičtější.

## <a name="using-winresexe"></a>Používání nástroje Winres.exe

Chcete-li lokalizovat pomocí Winres.exe, je třeba nejprve vytvořit aplikaci pomocí visual designer jako **Návrháře formulářů Windows** v sadě Visual Studio. Po dokončení vývoje formuláře nastavte <xref:System.ComponentModel.LocalizableAttribute> ( **Localizable** vlastnost v **vlastnosti** editor) na `true`a poté předejte soubor .resx s výchozí jazykové verze pro překladateli. Tento soubor .resx obsahuje další informace, které nástroj Winres.exe použije k obnovení verze návrhu původního formuláře.

> [!NOTE]
> Nástroj Winres.exe nelze použít k úpravě výchozího souboru prostředků. Nástroj Winres.exe interpretuje všechny změněné vlastnosti jako lokalizované vlastnosti a ukládá je do souboru prostředků cílové jazykové verze.

Konečné verze souborů prostředků jazykové verze lze nakonec použít k vytvoření lokalizovaných verzí aplikace. Další informace najdete v tématu [prostředky v desktopových aplikací](../../../docs/framework/resources/index.md).

Winres.exe obsahuje následující funkce a možnosti:

- Nástroj Winres může pracovat v režimu Single File Mode (SFM) nebo v režimu Visual Studio File Mode (VSFM). SFM je starší režim, ve kterém jsou úplné informace o formuláři a jeho obsahu uloženy do souboru prostředků. Režim VSFM ukládá pouze změny jazykové verze v souboru prostředků.

- Oknem hlášení chyb ukotvené v levé dolní části hlavního okna.

- Klávesové zkratky můžete zkontrolovat duplicitu: z **formátu** nabídky, klikněte na tlačítko **zkontrolovat klávesové zkratky** příkazu.

## <a name="version-compatibility"></a>Kompatibilita verzí

Měli byste použít verzi nástroje Winres.exe vydanou s rozhraním .NET Framework, kterou používáte. Následující tabulka uvádí kompatibilní verze:

|Visual Studio|.NET Framework|Winres.exe|
|-------------------|--------------------|----------------|
|Visual Studio .NET 2002|1.0|1.0|
|Visual Studio .NET 2003|1.1|1.1|
|Visual Studio 2005|2.0|2.0|
|Visual Studio 2008|3.0 a 3.5|3.0 a 3.5|
|Visual Studio 2010|4.0|4.0|
|Visual Studio 2017|4.6|4.6|

> [!NOTE]
> Ačkoli se režim VSFM vyznačuje výhodou kompatibility se sadou Visual Studio, tak vzhledem k tomu, že do souboru prostředků jsou uloženy pouze změněné hodnoty, nástroj Winres.exe vyžaduje, aby se soubory nadřazené aktuálnímu souboru prostředků nacházely ve stejném adresáři. Například úpravy `TestApp.de-DE.resources`, němčina v německém souboru prostředků, vyžaduje přítomnost výchozího souboru prostředků `TestApp.resx`a případně souboru prostředků neutrální jazykové verze, `TestApp.de.resources`.

## <a name="examples"></a>Příklady

### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Lokalizace souborů .resx nebo .resources spojených s formulářem

1.  Typ `winres` v developer command prompt pro spuštění Winres.exe.

2.  Výchozí soubor prostředků pro formulář určený k lokalizaci, klikněte na tlačítko **otevřete** příkaz **souboru** nabídky a přejděte na soubor otevřete.

     -nebo-

     Při spouštění nástroje Winres.exe do příkazového řádku zadejte název otevíraného souboru.

     Následující příkaz spustí Winres.exe a načte formulář přidružený k `TestApp.resx` v návrháři formuláře.

    ```
    winres TestApp.resx
    ```

     Následující příkaz spustí Winres.exe a načte formulář přidružený k `TestApp.resources` v návrháři formuláře.

    ```
    winres TestApp.resources
    ```

    > [!NOTE]
    > Jestliže je formulář, jehož prostředky upravujete, zděděným formulářem, sestavení obsahující zděděný formulář i sestavení obsahující odvozený formulář musí být zaregistrována v globální mezipaměti sestavení (GAC) nebo musí být umístěna ve stejném adresáři jako nástroj WinRes.exe. Další informace o instalaci komponent rozhraní .NET Framework do GAC naleznete v tématu [Global Assembly Cache](../../../docs/framework/app-domains/gac.md).

3.  Vyberte ovládací prvky ve formuláři a změnit jejich <xref:System.Windows.Forms.Control.Text%2A> a další vlastnosti tak, aby odrážely lokalizovanou jazykovou verzi a jazyk. Přesuňte ovládací prvky nebo změňte jejich velikost tak, aby vyhovovaly lokalizovanému textu.

4.  Lokalizovanou verzi souboru .resx nebo .resources uložte, klikněte na tlačítko **Uložit** ikony nebo stejný příkaz na **souboru** nabídky. Nástroj zobrazí **vyberte jazykovou verzi** okna.

5.  Vyberte odpovídající režim jazykové verze a soubor a klikněte na **OK**.

   Nástroj uloží soubor pomocí zásady vytváření názvů, který očekává, že čas spuštění pro lokalizované soubory prostředků. Například, pokud lokalizujete `TestApp.resources` do němčiny, nástroj uloží soubor jako `TestApp.de-DE.resources`. Pokud lokalizujete `TestApp.resx` do němčiny, nástroj uloží soubor jako `TestApp.de-DE.resx`. Další informace o vytváření názvů prostředků najdete v tématu [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Seznam předdefinovaných názvů jazykových používá čas spuštění, najdete v článku <xref:System.Globalization.CultureInfo> třídy.

## <a name="see-also"></a>Viz také:

- <xref:System.ComponentModel.LocalizableAttribute>
- <xref:System.Globalization.CultureInfo>
- <xref:System.Resources.ResourceManager>
- <xref:System.Resources.ResourceReader>
- <xref:System.Resources.ResourceWriter>
- [Nástroje](../../../docs/framework/tools/index.md)
- [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)
- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
