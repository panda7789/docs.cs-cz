---
title: Globalizace
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- globalization [.NET Framework], about globalization
- global applications, globalization
- international applications [.NET Framework], globalization
- world-ready applications, globalization
- application development [.NET Framework], globalization
- culture, globalization
ms.assetid: 4e919934-6b19-42f2-b770-275a4fae87c9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84e44f0112a5d1b5fd38daf488d865f6e228f82b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713938"
---
# <a name="globalization"></a>Globalizace
Globalizace zahrnuje návrh a vývoj globalizovaných aplikace, která podporuje lokalizovaná uživatelská rozhraní a regionální data pro uživatele ve více jazykových verzích. Před zahájením fáze návrhu, byste měli určit jazykové verze, které bude aplikace podporovat. Přestože aplikace cílí na jednu kulturu nebo oblast jako výchozí, můžete navrhnout a napsat ji tak, aby ho snadno rozšířitelná na uživatele v jiné jazykové verze nebo regiony.  
  
 Jako vývojáři máme všichni nějaké předpoklady o uživatelských rozhraních a datech, která jsou vytvářena našimi jazykovými verzemi. Například pro anglicky mluvící vývojáře ve Spojených státech amerických, serializaci jako řetězec ve formátu data a času `MM/dd/yyyy hh:mm:ss` zcela přiměřená. Deserializace tohoto řetězce v systému s jinou jazykovou verzí je však pravděpodobně vyvolá výjimku <xref:System.FormatException> výjimky nebo vygeneruje nesprávná data. Globalizace umožňuje identifikovat tyto jazykové předpoklady a ujistěte se, že nemají vliv na návrh nebo kód našich aplikací.  
  
 Následující části popisují některé hlavní problémy, které byste měli zvážit a doporučené postupy, které můžete použít při zpracování řetězců, datum a časové hodnoty a číselných hodnot v globalizovaných aplikacích.  
  
-   [Zpracování řetězců](../../../docs/standard/globalization-localization/globalization.md#HandlingStrings)  
  
    -   [Interní používání standardu Unicode](../../../docs/standard/globalization-localization/globalization.md#Strings_Unicode)  
  
    -   [Používání souborů prostředků](../../../docs/standard/globalization-localization/globalization.md#Strings_Resources)  
  
    -   [Vyhledávání a porovnávání řetězců ](../../../docs/standard/globalization-localization/globalization.md#Strings_Searching)  
  
    -   [Testování rovnosti řetězců](../../../docs/standard/globalization-localization/globalization.md#Strings_Equality)  
  
    -   [Řazení řetězců ](../../../docs/standard/globalization-localization/globalization.md#Strings_Ordering)  
  
    -   [Vyhněte se řetězení řetězců](../../../docs/standard/globalization-localization/globalization.md#Strings_Concat)  
  
-   [Zpracování dat a časů](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes)  
  
    -   [Trvalé uchovávání hodnot data a časy](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Persist)  
  
    -   [Zobrazení dat a časů](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Display)  
  
    -   [Serializace a zohlednění časového pásma](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_TimeZones)  
  
    -   [Data a času aritmetické operace](../../../docs/standard/globalization-localization/globalization.md#DatesAndTimes_Arithmetic)  
  
-   [Zpracování číselných hodnot](../../../docs/standard/globalization-localization/globalization.md#Numbers)  
  
    -   [Zobrazení číselných hodnot](../../../docs/standard/globalization-localization/globalization.md#Numbers_Display)  
  
    -   [Trvalé uchovávání číselných hodnot](../../../docs/standard/globalization-localization/globalization.md#Numbers_Persist)  
  
-   [Práce s nastavením specifické pro jazykovou verzi](../../../docs/standard/globalization-localization/globalization.md#Cultures)  
  
<a name="HandlingStrings"></a>   
## <a name="handling-strings"></a>Zpracování řetězců  
 Zpracování znaků a řetězce je centrálním středem pozornosti globalizace, protože každá jazyková verze nebo region může použít různé znaky a znakové sady a seřadit je jinak. Tato část obsahuje doporučení pro používání řetězců v globalizovaných aplikacích.  
  
<a name="Strings_Unicode"></a>   
### <a name="use-unicode-internally"></a>Interní používání standardu Unicode  
 Ve výchozím nastavení používá rozhraní .NET Framework řetězce Unicode. Řetězec s kódováním Unicode se skládá z nula, jeden nebo více <xref:System.Char> objektů, z nichž každý představuje jednotku kódu UTF-16. Existuje reprezentace Unicode pro téměř všechny znaky v každé znakové sady používané po celém světě.  
  
 Mnoho aplikací a operačních systémů, včetně operačního systému Windows, můžete použít také používat znakové stránky představující znakové sady. Znakové stránky obvykle obsahují standardní hodnoty ASCII od 0x00 do 0x7F a mapují další znaky ve zbývajících hodnotách od 0x80 do 0xFF. Výklad hodnot od 0x80 po 0xFF závisí na specifické znakové stránce. Z tohoto důvodu měli vyhnout použití znakových stránek v globalizované aplikaci, pokud je to možné.  
  
 Následující příklad ukazuje nebezpečí interpretace kódové stránky když výchozí kódová stránka v systému se liší od kódové stránky, na kterém byla uložena data. (Chcete-li simulovat tento scénář, příklad explicitně určuje různé znakové stránky.) Nejprve příklad definuje pole, které obsahuje velká písmena řecké abecedy. Zakóduje je do bajtového pole pomocí kódu stránky 737 (označované také jako řečtina zástupného kódu MS-DOS) a uloží do souboru bajtového pole. Pokud je soubor načten a jeho bajtové pole je dekódováno pomocí kódu stránky 737, budou obnoveny původní znaky. Nicméně pokud je soubor načten a jeho bajtové pole je dekódováno pomocí znaková stránka 1252 (nebo Windows-1252 představující znaky latinské abecedy), původní znaky budou ztraceny.  
  
 [!code-csharp[Conceptual.Globalization#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/codepages1.cs#1)]
 [!code-vb[Conceptual.Globalization#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/codepages1.vb#1)]  
  
 Použití kódování Unicode zajišťuje, že stejné jednotky kódu se vždy mapují na stejné znaky a že stejné znaky se vždy mapují na stejná pole bajtů.  
  
<a name="Strings_Resources"></a>   
### <a name="use-resource-files"></a>Používání souborů prostředků  
 I když vyvíjíte aplikaci, která se zaměřuje na jednu kulturu nebo oblast, používejte soubory prostředků pro uložení řetězců a dalších prostředků, které jsou zobrazeny v uživatelském rozhraní. Měli byste nikdy přidat je přímo do vašeho kódu. Použití souborů prostředků má několik výhod:  
  
-   Všechny řetězce jsou na jednom místě. Nemusíte hledat v celém zdrojovém kódu k identifikaci řetězců pro úpravu pro konkrétní jazyk nebo jazykovou verzi.  
  
-   Není nutné duplikovat řetězce. Vývojáři, kteří nepoužívají soubory prostředků často definují stejný řetězec ve více souborů zdrojového kódu. Tato duplikace zvyšuje pravděpodobnost, že jedna nebo více instancí bude přehlédnuta při úpravě řetězce.  
  
-   Neřetězcové prostředky, jako jsou obrázky nebo binární data, můžete zahrnout do souboru prostředků místo uložení do samostatného souboru, takže je možné snadno načíst.  
  
 Použití souborů prostředků má určité výhody, chcete-li vytvořit lokalizovanou aplikaci. Při nasazování prostředků v satelitních sestaveních, modul common language runtime automaticky vybere odpovídající jazykovou verzi prostředku podle uživatele aktuální jazykové verze uživatelského rozhraní definované <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost. Za předpokladu, zadejte odpovídající prostředek specifický pro jazykovou verzi a správně vytváříte instance <xref:System.Resources.ResourceManager> objektu nebo použití třídy prostředků se silnými typy, modul runtime zpracovává detaily o načtení příslušných prostředků.  
  
 Další informace o vytváření souborů prostředků naleznete v tématu [Creating Resource Files](../../../docs/framework/resources/creating-resource-files-for-desktop-apps.md). Informace o vytváření a nasazení satelitního sestavení naleznete v tématu [Vytváření satelitních sestavení](../../../docs/framework/resources/creating-satellite-assemblies-for-desktop-apps.md) a [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).  
  
<a name="Strings_Searching"></a>   
### <a name="searching-and-comparing-strings"></a>Vyhledávání a porovnávání řetězců  
 Kdykoli je to možné, zpracovávejte řetězce jako celé řetězce namísto jednotlivých znaků. To je zvlášť důležité při řazení nebo vyhledávání podřetězců, aby se zabránilo problémům spojeným s analýzou kombinovaných znaků.  
  
> [!TIP]
>  Můžete použít <xref:System.Globalization.StringInfo> tříd pro práci s elementy textu místo jednotlivých znaků v řetězci.  
  
 V řetězec hledání a porovnávání řetězců je obvyklou chybou považovat řetězec za kolekci znaků, z nichž každý je reprezentován <xref:System.Char> objektu. Ve skutečnosti může jeden znak tvořen jeden, dva nebo více <xref:System.Char> objekty. Tyto znaky jsou nejčastěji součástí řetězce z kultur, jejichž písmena abecedy jsou tvořena znaky mimo rozsah znaků základní latinky Unicode (U + 0021 až U + 007E). Následující příklad se pokusí vyhledat index znaku velké znak LATIN velké písmeno A s čárkou nad vlevo (U + 00C 0) v řetězci. Nicméně, tento znak může být reprezentován dvěma různými způsoby: jako jedna znaková jednotka (U + 00C 0) nebo jako složený znak (dvě znakové jednotky: U+ 0021 a U + 007E). V takovém případě je znak reprezentován v instanci řetězce dvěma <xref:System.Char> objektů, U + 0021 a U + 007E. Příklad kódu volá <xref:System.String.IndexOf%28System.Char%29?displayProperty=nameWithType> a <xref:System.String.IndexOf%28System.String%29?displayProperty=nameWithType> přetížení pro hledání pozice tohoto znaku v instanci řetězce, ale tyto vrací odlišné výsledky. První metoda volání má <xref:System.Char> argument; provádí řadové porovnání a proto nemůže nalézt shodu. Druhé volání má <xref:System.String> argument; provádí porovnání citlivé na jazykovou verzi a proto najde shodu.  
  
 [!code-csharp[Conceptual.Globalization#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/search1.cs#18)]
 [!code-vb[Conceptual.Globalization#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/search1.vb#18)]  
  
 Nejednoznačnosti tohoto příkladu (volání dvou samostatných přetížení metody vracející různé výsledky) můžete zabránit voláním přetížení, která zahrnuje <xref:System.StringComparison> parametr, například <xref:System.String.IndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> nebo <xref:System.String.LastIndexOf%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metoda.  
  
 Ale hledání nejsou vždy zohledňující jazykovou verzi. Pokud je účelem vyhledávání k rozhodování zabezpečení nebo k povolení nebo zakázání přístupu k některým zdrojům, srovnání by mělo být řádové, jak je popsáno v další části.  
  
<a name="Strings_Equality"></a>   
### <a name="testing-strings-for-equality"></a>Testování rovnosti řetězců  
 Pokud chcete otestovat dva řetězce pro rovnosti místo určení, jak je jejich srovnání v pořadí řazení, použijte <xref:System.String.Equals%2A?displayProperty=nameWithType> metoda namísto metody porovnání řetězců, jako <xref:System.String.Compare%2A?displayProperty=nameWithType> nebo <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType>.  
  
 Porovnání rovnosti se obvykle provádí pro přístup některých prostředků podmíněně. Můžete například provádět porovnání rovnosti a ověřit tak heslo nebo potvrďte, že soubor existuje. Tato nelingvistická porovnání by měl být vždy řadová, nikoli zohledňující jazykovou verzi. Obecně byste měli volat instanci <xref:System.String.Equals%28System.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody nebo statická <xref:System.String.Equals%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> metody s hodnotou <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> pro řetězce, jako jsou hesla a hodnota <xref:System.StringComparison.OrdinalIgnoreCase?displayProperty=nameWithType> pro řetězce, jako jsou názvy souborů nebo identifikátory URI.  
  
 Porovnání rovnosti někdy zahrnují vyhledávání nebo porovnání podřetězců, namísto volání <xref:System.String.Equals%2A?displayProperty=nameWithType> metody. V některých případech můžete použít hledání dílčího řetězce k určení, zda tento dílčí řetězec rovná jinému řetězci. Pokud účel nejazykové, vyhledávání by měla být řádové, nikoli zohledňující jazykovou verzi.  
  
 Následující příklad ukazuje nebezpečí při nelingvistických dat vyhledávání zohledňující jazykovou verzi. `AccessesFileSystem` Metody slouží k zákazu přístupu k systému souborů pro identifikátory URI, který začíná pod řetězcem "FILE". Chcete-li to provést, provede porovnání zohledňující jazykovou verzi, velká a malá písmena začátku identifikátoru URI s řetězcem "FILE". Protože identifikátor URI, který má přístup k systému souborů může začínat znakem "FILE:" nebo "souboru:", je implicitní předpoklad je, že "i" (U + 0069) je vždy malým ekvivalentem znaku "I" (U + 0049). Ale v turečtině a Ázerbájdžánština, velká písmena verzi "İ" je "i" (U + 0130). Kvůli této nesrovnalosti srovnání citlivé na jazykovou verzi umožňuje přístupu k systému souborů, když by mělo být zakázané.  
  
 [!code-csharp[Conceptual.Globalization#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals1.cs#12)]
 [!code-vb[Conceptual.Globalization#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals1.vb#12)]  
  
 Je-li předejít tomuto problému, provádí řadové porovnání, které ignoruje velikost písmen, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Globalization#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/equals2.cs#13)]
 [!code-vb[Conceptual.Globalization#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/equals2.vb#13)]  
  
<a name="Strings_Ordering"></a>   
### <a name="ordering-and-sorting-strings"></a>Řazení řetězců  
 Obvykle řazené řetězce, které se mají zobrazit v uživatelském rozhraní mají být řazeny podle jazykové verze. Ve většině případů porovnávání těchto řetězců zpracováváno implicitně pomocí rozhraní .NET Framework při volání metody, která řadí řetězce, jako například <xref:System.Array.Sort%2A?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType>. Ve výchozím nastavení jsou řetězce seřazeny pomocí konvence řazení pro aktuální jazykovou verzi. Následující příklad ukazuje rozdíl, když je pole řetězců seřazeno pomocí úmluv jazykové verze Angličtina (Spojené státy) a švédština (Švédsko) jazykovou verzi.  
  
 [!code-csharp[Conceptual.Globalization#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sort1.cs#14)]
 [!code-vb[Conceptual.Globalization#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sort1.vb#14)]  
  
 Porovnání řetězců zohledňující jazykovou verzi je definován <xref:System.Globalization.CompareInfo> objektu, který je vrácený každou jazykovou verzi <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> vlastnost. Porovnání řetězců zohledňující jazykovou verzi, které používají <xref:System.String.Compare%2A?displayProperty=nameWithType> přetížení metody také použití <xref:System.Globalization.CompareInfo> objektu.  
  
 Rozhraní .NET Framework používá k provedení řazení zohledňující jazykovou verzi na řetězec data tabulky. Obsah těchto tabulek, které obsahují údaje o řazení váhy a řetězci normalizace, závisí na verzi standard Unicode implementované konkrétní verzi rozhraní .NET Framework. V následující tabulce jsou uvedeny verze Unicode implementované zadanou verzí rozhraní .NET Framework. Všimněte si, že tento seznam podporovaných verzí sady Unicode se vztahuje na znak porovnání a řazení. To se nevztahují na klasifikaci znaků Unicode podle kategorie. Další informace najdete v tématu v části "Řetězců a ve standardu Unicode" <xref:System.String> článku.  
  
|Verze rozhraní .NET Framework|Operační systém|Verze Unicode|  
|----------------------------|----------------------|---------------------|  
|.NET Framework 2.0|Všechny operační systémy|4.1 kódování Unicode|  
|.NET Framework 3.0|Všechny operační systémy|4.1 kódování Unicode|  
|.NET Framework 3.5|Všechny operační systémy|4.1 kódování Unicode|  
|.NET Framework 4|Všechny operační systémy|Standard Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win7](../../../includes/win7-md.md)]|Standard Unicode 5.0|  
|.NET Framework 4.5|[!INCLUDE[win8](../../../includes/win8-md.md)]|Standard Unicode 6.0|  
  
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], porovnání a řazení řetězců závisí na operačním systému. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Systémem [!INCLUDE[win7](../../../includes/win7-md.md)] načte data ze svých tabulek, které implementují Standard Unicode 5.0. [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Systémem [!INCLUDE[win8](../../../includes/win8-md.md)] načítá data z tabulek operačního systému, které implementují Standard Unicode 6.0. Pokud serializujete seřazená data zohledňující jazykovou verzi, můžete použít <xref:System.Globalization.SortVersion> třídu k určení, kdy je potřeba serializovaná data seřadit tak, aby byla konzistentní s rozhraní .NET Framework a pořadí řazení operačního systému. Příklad najdete v tématu <xref:System.Globalization.SortVersion> třídě.  
  
 Pokud vaše aplikace provádí rozsáhlé řazení dat řetězců specifické pro jazykovou verzi, můžete pracovat <xref:System.Globalization.SortKey> třídy pro porovnání řetězců. Klíč řazení odráží váhu řazení specifický pro jazykovou verzi, včetně abecedy, případu a diakritických znamének určitého řetězce. Protože porovnání pomocí klíčů řazení jsou binární, jsou rychlejší než porovnání, která používají <xref:System.Globalization.CompareInfo> objektu implicitně nebo explicitně. Vytvořte klíč řazení specifický pro jazykovou verzi pro určitý řetězec předáním řetězce do <xref:System.Globalization.CompareInfo.GetSortKey%2A?displayProperty=nameWithType> metody.  
  
 Následující příklad je podobné jako v předchozím příkladu. Ale namísto volání metody <xref:System.Array.Sort%28System.Array%29?displayProperty=nameWithType> metoda, která volá implicitně <xref:System.Globalization.CompareInfo.Compare%2A?displayProperty=nameWithType> definuje metodu, <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace, která porovnává klíče řazení, které vytvoří instanci a předá <xref:System.Array.Sort%60%601%28%60%600%5B%5D%2CSystem.Collections.Generic.IComparer%7B%60%600%7D%29?displayProperty=nameWithType> – metoda.  
  
 [!code-csharp[Conceptual.Globalization#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/sortkey1.cs#15)]
 [!code-vb[Conceptual.Globalization#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/sortkey1.vb#15)]  
  
<a name="Strings_Concat"></a>   
### <a name="avoid-string-concatenation"></a>Vyhněte se řetězení řetězců  
 Pokud je to možné nepoužívejte složené řetězce, které jsou vytvořeny v době běhu ze spojených frází. Složené řetězce se obtížně lokalizují, protože často předpokládají gramatický sled v původním jazyce aplikace, který se nedá použít u jiných lokalizovaných jazyků.  
  
<a name="DatesAndTimes"></a>   
## <a name="handling-dates-and-times"></a>Zpracování hodnot data a času  
 Jak zpracovat data a času hodnoty závisí na tom, zda jsou zobrazeny v uživatelském rozhraní nebo trvalé. Tato část se zabývá obojím použitím. Také popisuje, jak můžete zpracovávat rozdíly v časových pásmech a aritmetické operace při práci s daty a časy.  
  
<a name="DatesAndTimes_Display"></a>   
### <a name="displaying-dates-and-times"></a>Zobrazení hodnot data a času  
 Obvykle, když data a časy jsou zobrazeny v uživatelském rozhraní, byste měli použít formátovacích úmluv jazykové verze uživatele, který je definovaný <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Globalization.DateTimeFormatInfo> vrácený `CultureInfo.CurrentCulture.DateTimeFormat` vlastnost. Formátovacích úmluv aktuální jazykové verze automaticky používá, když formátujete datum pomocí některé z těchto metod:  
  
-   Bezparametrová <xref:System.DateTime.ToString?displayProperty=nameWithType> – metoda  
  
-   <xref:System.DateTime.ToString%28System.String%29?displayProperty=nameWithType> Metodu, která obsahuje formátovací řetězec  
  
-   Bezparametrová <xref:System.DateTimeOffset.ToString?displayProperty=nameWithType> – metoda  
  
-   <xref:System.DateTimeOffset.ToString%28System.String%29?displayProperty=nameWithType>, Která obsahuje formátovací řetězec  
  
-   [Složené formátování](../../../docs/standard/base-types/composite-formatting.md) funkce, když se používá s daty  
  
 Následující příklad zobrazí data o východu a západu slunce dvakrát pro 11. října 2012. Nejprve nastaví aktuální jazykovou verzi na možnost Chorvatština (Chorvatsko) a angličtina (Velká Británie). V každém případě jsou data a časy jsou zobrazeny ve formátu, který je vhodný pro danou jazykovou verzi.  
  
 [!code-csharp[Conceptual.Globalization#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates1.cs#2)]
 [!code-vb[Conceptual.Globalization#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates1.vb#2)]  
  
<a name="DatesAndTimes_Persist"></a>   
### <a name="persisting-dates-and-times"></a>Trvalé uchovávání hodnot data a času  
 Nikdy byste neměli zachovat data datum a čas ve formátu, který se může lišit podle jazykové verze. Toto je běžná programovací chyba, jejímž výsledkem poškození dat nebo výjimce za běhu. Následující příklad serializuje dvě data, 9. lednu 2013 a 18. srpna 2013 jako řetězce pomocí formátovacích úmluv jazykové verze Angličtina (Spojené státy). Když data načtena a analyzována pomocí úmluv jazykové verze Angličtina (Spojené státy), se úspěšně obnovila. Ale když ho načtena a analyzována pomocí úmluv jazykové verze Angličtina (Spojené království), první datum je nesprávně interpretováno jako 1. září a druhé se nepodaří analyzovat, protože gregoriánský kalendář nemá osmnáct měsíců.  
  
 [!code-csharp[Conceptual.Globalization#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates2.cs#3)]
 [!code-vb[Conceptual.Globalization#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates2.vb#3)]  
  
 Možné předejít tomuto problému v libovolné ze tří způsobů:  
  
-   Serializujte datum a čas v binárním formátu, nikoli jako řetězec.  
  
-   Uložit a analyzovat řetězcové vyjádření data a času s použitím vlastní formátovací řetězec, který je stejný bez ohledu na jazykovou verzi uživatele.  
  
-   Uložte řetězec pomocí formátovacích úmluv invariantní jazykové verze.  
  
 Následující příklad ukazuje poslední přístup. Používá konvence formátování invariantní jazykové verze vrácené statickou <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
 [!code-csharp[Conceptual.Globalization#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates3.cs#4)]
 [!code-vb[Conceptual.Globalization#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates3.vb#4)]  
  
<a name="DatesAndTimes_TimeZones"></a>   
### <a name="serialization-and-time-zone-awareness"></a>Serializace a zohlednění časového pásma  
 Hodnoty data a času může mít více interpretací, od obecného časového ("obchody otevřít 2. ledna 2013 v 9:00") pro určitý okamžik v čase ("datum narození: 2. ledna 2013 6:32:00 dop."). Když časová hodnota představuje určitý okamžik v čase a obnovíte ji ze serializované hodnoty, měli byste zajistit, že představuje stejný okamžik v čase bez ohledu na zeměpisnou polohu nebo časové pásmo uživatele.  
  
 Následující příklad ukazuje tento problém. Uloží jedné místní hodnotu data a času jako řetězec ve třech [standardní formáty](../../../docs/standard/base-types/standard-date-and-time-format-strings.md) ("G" pro obecné datum a dlouhý čas, "s" pro seřaditelné datum a čas a "o" pro operace round-trip pro datum/čas) i v binárním formátu.  
  
 [!code-csharp[Conceptual.Globalization#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates4.cs#10)]
 [!code-vb[Conceptual.Globalization#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates4.vb#10)]  
  
 Při obnovení dat v systému ve stejném časovém pásmu jako systém, na kterém byla serializována deserializované hodnoty data a času přesně odrážejí původní hodnotu, jak ukazuje výstup:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/30/2013 6:00:00 PM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 Pokud ale můžete obnovit data v rámci systému v jiném časovém pásmu, pouze hodnoty data a času, který se naformátoval pomocí standardního formátovacího řetězce "o" (round-trip) uchovává informace o časovém pásmu a proto představuje stejný instantní v čase. Při obnovení dat data a času v systému ve Středoevropském časovém pásmu, zde je výstup:  
  
```  
'3/30/2013 6:00:00 PM' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00' --> 3/30/2013 6:00:00 PM Unspecified  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
  
3/30/2013 6:00:00 PM Local  
```  
  
 K přesnému vyjádření hodnoty data a času, který představuje jeden okamžiku v čase bez ohledu na časové pásmo systému, na kterém jsou data deserializována, proveďte některý z následujících akcí:  
  
-   Uložte hodnotu jako řetězec pomocí řetězce "o" (round-trip) standardního formátu. Pak ho Deserializujte v cílovém systému.  
  
-   Převeďte jej na UTC a uložte ho jako řetězec pomocí standardního formátovacího řetězce "r" (RFC1123). Pak ho Deserializujte v cílovém systému a převeďte ji na místní čas.  
  
-   Převeďte jej na UTC a uložte ho jako řetězec pomocí standardního formátovacího řetězce "u" (Univerzální seřaditelný). Pak ho Deserializujte v cílovém systému a převeďte ji na místní čas.  
  
-   Převeďte jej na UTC a uložte v binárním formátu. Pak ho Deserializujte v cílovém systému a převeďte ji na místní čas.  
  
 Následující příklad každou techniku ukazuje.  
  
 [!code-csharp[Conceptual.Globalization#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates8.cs#11)]
 [!code-vb[Conceptual.Globalization#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates8.vb#11)]  
  
 Když se data serializována v systému ve standardním tichomořském časovém pásmu a deserializována v systému ve Středoevropském časovém pásmu, v příkladu se zobrazí následující výstup:  
  
```  
'2013-03-30T18:00:00.0000000-07:00' --> 3/31/2013 3:00:00 AM Local  
'Sun, 31 Mar 2013 01:00:00 GMT' --> 3/31/2013 3:00:00 AM Local  
'2013-03-31 01:00:00Z' --> 3/31/2013 3:00:00 AM Local  
  
3/31/2013 3:00:00 AM Local  
```  
  
 Další informace najdete v tématu [převod časy mezi časovými pásmy](../../../docs/standard/datetime/converting-between-time-zones.md).  
  
<a name="DatesAndTimes_Arithmetic"></a>   
### <a name="performing-date-and-time-arithmetic"></a>Aritmetické operace s hodnotami data a času  
 Jak <xref:System.DateTime> a <xref:System.DateTimeOffset> typů podporuje aritmetické operace. Můžete vypočítat rozdíl mezi dvěma hodnotami data nebo můžete přičíst nebo odečíst konkrétní časové intervaly k nebo od hodnoty data. Ale aritmetické operace na hodnoty data a času nepřebírají časových pásmech a pravidla úpravy časového pásma v úvahu. Z tohoto důvodu aritmetika na hodnotách, které představují momenty v čase data a času může vracet nepřesné výsledky.  
  
 Například přechodu ze standardního tichomořského času na pacifický letní čas proběhne druhou neděli v březnu, což je 10 dne v roce 2013. Jako následující příklad ukazuje, je-li vypočítat datum a čas, který je 48 hodin od 9. března 2013 v 10:30 hod v systému ve standardním tichomořském časovém pásmu výsledek, 11. března 2013 v 10:30 hod, nepřijímá potaz úpravu zasahující čas.  
  
 [!code-csharp[Conceptual.Globalization#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates5.cs#8)]
 [!code-vb[Conceptual.Globalization#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates5.vb#8)]  
  
 Aby bylo zajištěno, že aritmetické operace na hodnoty data a času vytváří přesné výsledky, postupujte podle těchto kroků:  
  
1.  Převeďte na čas UTC čas v časovém pásmu zdroje.  
  
2.  Proveďte aritmetickou operaci.  
  
3.  Pokud je výsledkem hodnota data a času, převeďte ji z času UTC na čas v časovém pásmu zdroje.  
  
 Následující příklad je podobné jako v předchozím příkladu, s tím rozdílem, že následuje tyto tři kroky pro správné přidání 48 hodin k 9 březnu 2013 v 10:30 hod  
  
 [!code-csharp[Conceptual.Globalization#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/dates6.cs#9)]
 [!code-vb[Conceptual.Globalization#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/dates6.vb#9)]  
  
 Další informace najdete v tématu [provádí aritmetické operace s daty a časy](../../../docs/standard/datetime/performing-arithmetic-operations.md).  
  
### <a name="using-culture-sensitive-names-for-date-elements"></a>Používání názvů zohledňujících jazykovou verzi pro elementy kalendářního data  
 Vaše aplikace může potřebovat zobrazit název měsíce nebo den v týdnu. K tomu dochází například následující kód.  
  
 [!code-csharp[Conceptual.Globalization#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname1.cs#19)]
 [!code-vb[Conceptual.Globalization#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname1.vb#19)]  
  
 Tento kód však vždy vrací názvy dnů v týdnu v angličtině. Kód, který získává název měsíce je často mnohem více neflexibilní. Často se předpokládá dvanáctiměsíční kalendář s názvy měsíců v určitém jazyce.  
  
 S použitím [řetězce formátu vlastní data a času](../../../docs/standard/base-types/custom-date-and-time-format-strings.md) nebo vlastnosti <xref:System.Globalization.DateTimeFormatInfo> objekt, je lze snadno extrahovat řetězce, které obsahují názvy dnů v týdnu nebo měsíců v jazykové verzi uživatele, jak ukazuje následující příklad. Změní aktuální jazykovou verzi na Francouzština (Francie) a zobrazí název dne v týdnu a názvu měsíce pro 1. července 2013.  
  
 [!code-csharp[Conceptual.Globalization#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/monthname2.cs#20)]
 [!code-vb[Conceptual.Globalization#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/monthname2.vb#20)]  
  
<a name="Numbers"></a>   
## <a name="handling-numeric-values"></a>Zpracování číselných hodnot  
 Zpracování čísel závisí na tom, zda jsou zobrazeny v uživatelském rozhraní nebo trvalé. Tato část se zabývá obojím použitím.  
  
> [!NOTE]
>  V operacích analýzy a formátování, rozpozná rozhraní .NET Framework pouze základní znaky latinky 0 až 9 (U + 0030 až U + 0039) jako číselné znaky.  
  
<a name="Numbers_Display"></a>   
### <a name="displaying-numeric-values"></a>Zobrazení číselných hodnot  
 Obvykle, když jsou čísla zobrazena v uživatelském rozhraní, byste měli použít formátovacích úmluv jazykové verze uživatele, který je definovaný <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> vlastnosti a <xref:System.Globalization.NumberFormatInfo> vrácený `CultureInfo.CurrentCulture.NumberFormat` vlastnost. Formátovacích úmluv aktuální jazykové verze automaticky používá, když formátujete datum pomocí některé z následujících metod:  
  
-   Bezparametrová `ToString` metoda libovolného číselného typu  
  
-   `ToString(String)` Metoda libovolného číselného typu, která obsahuje formátovací řetězec jako argument  
  
-   [Složené formátování](../../../docs/standard/base-types/composite-formatting.md) funkce, když se používá s číselnými hodnotami  
  
 Následující příklad zobrazuje průměrnou teplota za měsíc v Paříž, Francie. Nejprve nastaví aktuální jazykovou verzi na Francouzština (Francie) před zobrazením dat a nastaví ji na angličtinu (Spojené státy). V každém případě jsou názvy měsíců a teploty zobrazeny ve formátu, který je vhodný pro danou jazykovou verzi. Všimněte si, že tyto dvě jazykové verze používají různé oddělovače desetinných míst v hodnotě teploty. Všimněte si také, že v příkladu používá "MMMM" vlastní datum a čas řetězec formátu k zobrazení celého názvu měsíce a že přidělí odpovídající množství místa pro název měsíce ve výsledném řetězci určením délky nejdelší názvu měsíce v <xref:System.Globalization.DateTimeFormatInfo.MonthNames%2A?displayProperty=nameWithType></C0>pole.  
  
 [!code-csharp[Conceptual.Globalization#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers1.cs#5)]
 [!code-vb[Conceptual.Globalization#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers1.vb#5)]  
  
<a name="Numbers_Persist"></a>   
### <a name="persisting-numeric-values"></a>Trvalé uchovávání číselných hodnot  
 Nikdy byste neměli zachovat číselná data ve formátu specifické pro jazykovou verzi. Toto je běžná programovací chyba, jejímž výsledkem poškození dat nebo výjimce za běhu. Následující příklad generuje deset náhodných čísel s plovoucí desetinnou čárkou a serializuje je jako řetězce pomocí formátovacích úmluv jazykové verze Angličtina (Spojené státy). Když data načtena a analyzována pomocí úmluv jazykové verze Angličtina (Spojené státy), se úspěšně obnovila. Ale když je načten a analyzován pomocí konvencí jazykovou verzi francouzština (Francie), žádná čísla můžete analyzovat, protože kultury používají jiné oddělovače desetinných míst.  
  
 [!code-csharp[Conceptual.Globalization#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers2.cs#6)]
 [!code-vb[Conceptual.Globalization#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers2.vb#6)]  
  
 K tomuto problému vyhnout, můžete použít některý z následujících postupů:  
  
-   Uložit a analyzovat řetězcové vyjádření čísla pomocí řetězce vlastního formátu, který je stejný bez ohledu na jazykovou verzi uživatele.  
  
-   Uložit číslo jako řetězec pomocí formátovacích úmluv invariantní jazykové verze, která je vrácena <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> vlastnost.  
  
-   Serializujte číslo do binárního formátu místo formátu řetězce.  
  
 Následující příklad ukazuje poslední přístup. Dojde k serializaci pole <xref:System.Double> hodnoty a deserializuje zobrazí pomocí konvencí formátování jazykové verze francouzština (Francie) a angličtina (Spojené státy).  
  
 [!code-csharp[Conceptual.Globalization#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/numbers3.cs#7)]
 [!code-vb[Conceptual.Globalization#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/numbers3.vb#7)]  
  
 Serializace hodnot měny je zvláštní případ. Protože hodnota měny závisí na jednotce měny, ve kterém je vyjádřena; nemá příliš smysl s ní zacházet jako s nezávislou číselnou hodnotou. Nicméně pokud uložíte hodnotu měny jako formátovaný řetězec, který obsahuje symbol měny, ho nejde deserializovat v systému, jehož výchozí jazyková verze používá odlišný symbol měny, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Globalization#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency1.cs#16)]
 [!code-vb[Conceptual.Globalization#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency1.vb#16)]  
  
 Místo toho byste měli serializovat číselnou hodnotu spolu s některými informacemi o, jako je například název jazykové verze, tak, aby hodnotu a její symbol měny bylo možné deserializovat nezávisle aktuální jazykové verze. Následující příklad, který nemá definováním `CurrencyValue` struktura se dvěma členy: <xref:System.Decimal> hodnota a název jazykové verze, do které patří hodnota.  
  
 [!code-csharp[Conceptual.Globalization#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.globalization/cs/currency2.cs#17)]
 [!code-vb[Conceptual.Globalization#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.globalization/vb/currency2.vb#17)]  
  
<a name="Cultures"></a>   
## <a name="working-with-culture-specific-settings"></a>Práce s nastaveními specifickými pro jazykovou verzi  
 V rozhraní .NET Framework <xref:System.Globalization.CultureInfo> třída představuje konkrétní jazykovou verzi nebo oblast. Některé vlastnosti vrátí objekty, které obsahují podrobné informace o určitém aspektu kultury:  
  
-   <xref:System.Globalization.CultureInfo.CompareInfo%2A?displayProperty=nameWithType> Vrátí vlastnost <xref:System.Globalization.CompareInfo> objekt, který obsahuje informace o tom, jak kultura porovnává a objednává řetězce.  
  
-   <xref:System.Globalization.CultureInfo.DateTimeFormat%2A?displayProperty=nameWithType> Vrátí vlastnost <xref:System.Globalization.DateTimeFormatInfo> , který poskytuje informace specifické pro jazykovou verzi použitou při formátování data a času.  
  
-   <xref:System.Globalization.CultureInfo.NumberFormat%2A?displayProperty=nameWithType> Vrátí vlastnost <xref:System.Globalization.NumberFormatInfo> , který poskytuje informace specifické pro jazykovou verzi použitou při formátování číselná data.  
  
-   <xref:System.Globalization.CultureInfo.TextInfo%2A?displayProperty=nameWithType> Vrátí vlastnost <xref:System.Globalization.TextInfo> systému zápisu, který poskytuje informace o jazykové verzi.  
  
 Obecně není vhodné dělat závěry ohledně hodnot konkrétních <xref:System.Globalization.CultureInfo> vlastností a jejich souvisejících objektů. Místo toho by měl zobrazit data specifická pro jazykovou verzi jako proměnlivá z těchto důvodů:  
  
-   Hodnoty jednotlivých vlastností se mohou měnit s postupem času, jak opravit data, dat nebo změnami konvencí specifických pro jazykovou verzi.  
  
-   Hodnoty jednotlivých vlastností se mohou lišit mezi verzemi verze rozhraní .NET Framework nebo operačního systému.  
  
-   Rozhraní .NET Framework podporuje náhradní jazykové verze. Díky tomu je možné definovat nové vlastní jazykové verze, které doplňují stávající standardní jazykové verze nebo zcela nahrazují stávající standardní jazykovou verzi.  
  
-   Uživatel může upravit nastavení specifické pro jazykovou verzi pomocí **oblast a jazyk** aplikace v Ovládacích panelech. Při vytváření instance <xref:System.Globalization.CultureInfo> objektu, můžete určit, zda odráží tyto úpravy uživatele voláním <xref:System.Globalization.CultureInfo.%23ctor%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> konstruktoru. Obvykle pro aplikace koncových uživatelů měli respektovat uživatelské předvolby tak, aby uživatel dostal data ve formátu, který očekává.  
  
## <a name="see-also"></a>Viz také:

- [Globalizace a lokalizace](../../../docs/standard/globalization-localization/index.md)
- [Doporučené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md)
