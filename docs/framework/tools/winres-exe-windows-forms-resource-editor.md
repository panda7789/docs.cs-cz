---
title: Winres.exe (editor prostředků Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- Winres.exe
- Windows Forms Resource Editor
- localization
- Windows Forms, localization
- forms, localizing
- resx files
- .resx files
ms.assetid: cb8bc835-9221-4888-af53-1a4f5fad6c48
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 69ba816e5b7cf05ef094153b7ff044d573ac1760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="winresexe-windows-forms-resource-editor"></a>Winres.exe (editor prostředků Windows Forms)
Windows Forms Resource Editor (Winres.exe) je nástroj pro tvorbu vizuálního rozložení, který pomáhá odborníkům přes lokalizaci lokalizovat prostředky uživatelského rozhraní (UI) nástroje Windows Forms používané formuláři. Soubor prostředků .resx nebo .resources sloužící jako vstup do nástroje Winres.exe lze vytvořit pomocí prostředí pro vizuální návrh, jako je například sada Microsoft Visual Studio. Informace o nasazení prostředků v aplikacích rozhraní .NET Framework, najdete v části [prostředků v aplikacích plochy](../../../docs/framework/resources/index.md).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
winres resourceFile   
winres /?   
```  
  
## <a name="remarks"></a>Poznámky  
  
|Argument|Popis|  
|--------------|-----------------|  
|`resourceFile`|Soubor prostředků k lokalizaci. Tento soubor musí být formulář Windows Forms s příponou .resx nebo .resources vygenerovaný pomocí návrháře sady Visual Studio. Nástroj Winres.exe nedokáže otevřít obecné soubory .resx nebo .resources.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
 Stavy prvků UI z formuláře v projektu Windows Forms jsou obvykle uloženy v souborech prostředků s příponou .resx založených na XML nebo v souborech odpovídajících zkompilovaných binárních verzí s příponou .resources. Winres.exe je nástroj umožňující omezené úpravy obou typů souborů mimo návrhové prostředí sady Visual Studio. Konkrétně umožňuje následující typy operací úprav:  
  
-   Chcete-li změnit vlastnosti uživatelského rozhraní (UI) formuláře, můžete upravit soubor prostředků neutrální nebo konkrétní jazykové verze nebo jeho ovládací prvky jako například text, velikost či umístění.  
  
-   Soubory prostředků neutrální nebo konkrétní jazykové verze mohou být generovány z výchozího souboru prostředků.  
  
-   Soubor prostředků jazykové verze lze uložit jako soubor prostředků jiné jazykové verze. Například soubor prostředků pro angličtinu (USA) může být uložen jako soubor prostředků pro polštinu. Nový soubor bude obvykle upraven tak, aby byl kompatibilní s novou jazykovou verzí.  
  
 Viz také [hierarchická organizace zdrojů pro lokalizaci](http://msdn.microsoft.com/library/756hydy4\(v=vs.110\)) nebo [hierarchická organizace zdrojů pro lokalizaci](http://msdn.microsoft.com/library/756hydy4\(v=vs.120\)).  
  
 Nástroj Winres.exe nemůže převést soubor .resx na dopovídající soubor .resources; použijte místo něj nástroj Resgen.exe. Další informace o Resgen.exe najdete v tématu [Resgen.exe (Generátor zdrojových souborů)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).  
  
 Nástroj Winres.exe je grafická aplikace, která obnoví verzi návrhu formuláře Windows Forms pouze ze souboru prostředků, aniž by měla přístup ke zdrojovému kódu. Nástroj Winres.exe obsahuje nástroj Windows Forms Form Designer ze sady Visual Studio a okno Vlastnosti. Tyto funkce umožňují provádět vizuální úpravy souboru .resources nebo .resx obsahujícího formulář Windows Forms. Lokalizátoři obvykle používají nástroj Winres.exe k úpravě popisků ovládacích prvků a nastavení umístění a velikosti ovládacích prvků tak, aby vyhovovaly velikosti popisků cílové jazykové verze.  
  
 Pokud nástroj Winres.exe nedokáže rozlišit verzi ovládacího prvku, vytvoří v lokalizovaném souboru .resx nebo .resources zástupný text ovládacího prvku. Zástupný text ovládacího prvku se zobrazí ve formuláři Windows Forms jako šrafované okno. Velikost a umístění šrafovaného okna odpovídá skutečnému ovládacímu prvku. Všechny dostupné lokalizovatelné vlastnosti zástupného textu ovládacího prvku se zobrazí v okně Vlastnosti. Veškeré změny provedené v zástupném textu ovládacího prvku se uloží pro skutečný ovládací prvek.  
  
## <a name="winresexe-versus-visual-studio"></a>Srovnání nástroje Winres.exe a sady Visual Studio  
 Obecně platí, že dříve než začnete lokalizovat formuláře Windows Forms pro určitou aplikaci, měli byste se rozhodnout, zda chcete k lokalizaci použít sadu Visual Studio, nebo nástroj Winres.exe. Kompatibilita verzí, jak je popsáno dále, může bránit přepínání z jednoho nástroje na druhý.  
  
 Výhodou sady Visual Studio je, že ji můžete použít k vývoji i lokalizaci aplikace. O lokalizaci formuláře, po dokončení vývoj, nastavte jeho <xref:System.ComponentModel.LocalizableAttribute> ( **Localizable** vlastnost v editoru vlastnosti) k `true` a změňte jeho **jazyk** vlastnost, která má požadované cílové jazykové verzi. Poté změňte řetězce a upravte umístění a velikost ovládacích prvků tak, aby vyhovovaly řetězcům cílové jazykové verze. Při ukládání lokalizovaného souboru .resx sada Visual Studio do souboru zapíše pouze lokalizovatelné vlastnosti (vlastnosti, které se v cílové jazykové verzi změnily). Sada Visual Studio automaticky vytvoří satelitní sestavení pro lokalizovaný soubor .resx ve správném adresáři.  Viz také [návod: lokalizace Windows Forms](http://msdn.microsoft.com/library/y99d1cd3\(v=vs.110\)).  
  
 Přestože sada Visual Studio poskytuje integrované vývojové a lokalizační prostředí, v případě, že lokalizaci budou provádět externí překladatelé, doporučujeme použít nástroj Winres.exe. Protože Winres.exe je pouze lokalizační nástroj, umožňuje jasnější oddělení kódu aplikace od formulářů určených k lokalizaci, což je při řízení velkých projektů praktičtější.  
  
## <a name="using-winresexe"></a>Používání nástroje Winres.exe  
 Abyste mohli provádět lokalizaci pomocí nástroje Winres.exe, je třeba nejprve vytvořit aplikaci pomocí návrháře, jako je například nástroj Návrhář v sadě Visual Studio. Po dokončení vývoj nastavit formuláře <xref:System.ComponentModel.LocalizableAttribute> ( **Localizable** vlastnost v editoru vlastnosti) k `true`a pak předá soubor .resx pro výchozí jazykovou verzi na lokalizátora třetích stran. Tento soubor .resx obsahuje další informace, které nástroj Winres.exe použije k obnovení verze návrhu původního formuláře.  
  
> [!CAUTION]
>  Nástroj Winres.exe nelze použít k úpravě výchozího souboru prostředků. Nástroj Winres.exe interpretuje všechny změněné vlastnosti jako lokalizované vlastnosti a ukládá je do souboru prostředků cílové jazykové verze.  
  
 Konečné verze souborů prostředků jazykové verze lze nakonec použít k vytvoření lokalizovaných verzí aplikace. Další informace najdete v tématu [prostředků v aplikacích plochy](../../../docs/framework/resources/index.md).  
  
 Nástroj Winres.exe verze 2.0 obsahuje následující funkce a možnosti:  
  
-   Nástroj Winres může pracovat v režimu Single File Mode (SFM) nebo v režimu Visual Studio File Mode (VSFM). SFM je starší režim, ve kterém jsou úplné informace o formuláři a jeho obsahu uloženy do souboru prostředků. Režim VSFM ukládá pouze změny jazykové verze v souboru prostředků.  
  
-   Do rozhraní bylo přidáno okno hlášení chyb ukotvené v levé dolní části hlavního okna.  
  
-   Klávesové zkratky jde Zkontrolovat duplikáty: z nabídky Formát, klikněte na tlačítko **zkontrolovat klávesové zkratky** příkaz.  
  
## <a name="version-compatibility"></a>Kompatibilita verzí  
 Protože došlo ke změně formátu souborů prostředků mezi sadou Visual Studio .NET 2002 a Visual Studio 2005, nástroj Winres.exe byl rovněž změněn tak, aby byla zajištěna kompatibilita. Proto byste měli používat verzi nástroje Winres.exe vydanou s rozhraním .NET Framework, které používáte k vytvoření aplikace. Následující tabulka uvádí kompatibilní verze.  
  
|Visual Studio|.NET Framework|Winres.exe|  
|-------------------|--------------------|----------------|  
|Visual Studio .NET 2002|1.0|1.0|  
|Visual Studio .NET 2003|1.1|1.1|  
|Visual Studio 2005|2.0|2.0|  
|Visual Studio 2008|3.0 a 3.5|3.0 a 3.5|  
|Visual Studio 2010|4.0|4.0|  
  
 Pokud se pokusíte otevřít starší soubor prostředků v nástroji Winres.exe verze 2.0, budete vyzváni k upgradu na formát souboru, který bude kompatibilní s rozhraním .NET Framework verze 2.0.  
  
 Ve verzích rozhraní .NET Framework starších než verze 2.0 nástroj Winres.exe a Návrhář formulářů sady Visual Studio vytváří nekompatibilní soubory prostředků nezávislé a závislé na jazykové verzi. Proto, jakmile zahájíte proces lokalizace, musíte pokračovat pouze se stejným nástrojem. V nástroji Winres.exe verze 2.0 byl přidán režim Visual Studio File Mode (VSFM). Jak již název napovídá, soubor prostředků uložený v tomto režimu kompatibility lze upravovat pomocí kteréhokoli z těchto nástrojů.  
  
> [!NOTE]
>  Ačkoli se režim VSFM vyznačuje výhodou kompatibility se sadou Visual Studio, tak vzhledem k tomu, že do souboru prostředků jsou uloženy pouze změněné hodnoty, nástroj Winres.exe vyžaduje, aby se soubory nadřazené aktuálnímu souboru prostředků nacházely ve stejném adresáři. Například úpravy `TestApp.de-DE.resources`, němčina v souboru prostředků Německo, vyžaduje výchozí soubor prostředků `TestApp.resx`a pravděpodobně se soubor prostředků neutrální jazykové verze `TestApp.de.resources`.  
  
## <a name="examples"></a>Příklady  
  
#### <a name="to-localize-a-resx-or-resources-file-associated-with-a-form"></a>Lokalizace souborů .resx nebo .resources spojených s formulářem  
  
1.  Typ `winres` v příkazovém řádku vývojáře ke spuštění Winres.exe.  
  
2.  Chcete-li otevřít výchozí prostředky pro formulář k lokalizaci, klikněte na tlačítko **otevřete** příkaz na **souboru** nabídky a přejděte k souboru a ten se otevře.  
  
     -nebo-  
  
     Při spouštění nástroje Winres.exe do příkazového řádku zadejte název otevíraného souboru.  
  
     Tento příkaz spustí Winres.exe a načte formulář přidružený `TestApp.resx` v návrháři formuláře.  
  
    ```  
    winres TestApp.resx  
    ```  
  
     Tento příkaz spustí Winres.exe a načte formulář přidružený `TestApp.resources` v návrháři formuláře.  
  
    ```  
    winres TestApp.resources  
    ```  
  
    > [!NOTE]
    >  Jestliže je formulář, jehož prostředky upravujete, zděděným formulářem, sestavení obsahující zděděný formulář i sestavení obsahující odvozený formulář musí být zaregistrována v globální mezipaměti sestavení (GAC) nebo musí být umístěna ve stejném adresáři jako nástroj WinRes.exe. Další informace o instalaci součásti rozhraní .NET Framework do mezipaměti GAC najdete v tématu [globální mezipaměti sestavení](../../../docs/framework/app-domains/gac.md).  
  
3.  Vyberte ovládací prvky na formuláři a změnit jejich <xref:System.Windows.Forms.Control.Text%2A> a dalších vlastností tak, aby odrážela lokalizované jazykovou verzi a její jazyk. Přesuňte ovládací prvky nebo změňte jejich velikost tak, aby vyhovovaly lokalizovanému textu.  
  
4.  Lokalizované verzi souboru RESX nebo .resources uložit, klikněte **Uložit** ikony nebo stejný příkaz na **souboru** nabídky. Nástroj zobrazí **vyberte jazykovou verzi** okno.  
  
5.  Vyberte odpovídající režim jazykovou verzi a soubor a klikněte na **OK**. Nástroj uloží soubor s použitím konvence vytváření názvů, kterou modul pro lokalizované soubory prostředků očekává. Například, pokud je lokalizovat `TestApp.resources` pro němčinu v Německu nástroj uloží soubor jako `TestApp.de-DE.resources`. Pokud je lokalizovat `TestApp.resx` pro němčinu v Německu nástroj uloží soubor jako `TestApp.de-DE.resx`. Další informace o zásady vytváření názvů prostředků najdete v tématu [balení a nasazení prostředků](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md). Seznam předdefinovaných jazykovou verzi názvy používané čas spuštění, naleznete v části <xref:System.Globalization.CultureInfo> třídy.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.LocalizableAttribute>  
 <xref:System.Globalization.CultureInfo>  
 <xref:System.Resources.ResourceManager>  
 <xref:System.Resources.ResourceReader>  
 <xref:System.Resources.ResourceWriter>  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Prostředky v desktopových aplikacích](../../../docs/framework/resources/index.md)  
 [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
