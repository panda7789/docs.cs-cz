---
title: Třída XAMLServices a základní čtení a zápis v jazyku XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], XamlServices class
- XamlServices class [XAML Services], how to use
ms.assetid: 6ac27fad-3687-4d7a-add1-3e90675fdfde
ms.openlocfilehash: 264a8c4abcf9a7efceb7c7accd786495d35476e5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071876"
---
# <a name="xamlservices-class-and-basic-xaml-reading-or-writing"></a>Třída XAMLServices a základní čtení nebo zápis XAML

<xref:System.Xaml.XamlServices>je třída poskytovaná rozhraním .NET, kterou lze použít k řešení scénářů XAML, které nevyžadují specifický přístup k datovému proudu uzlu XAML nebo k informacím o systému typu XAML získaným z těchto uzlů. <xref:System.Xaml.XamlServices>Rozhraní API lze shrnout `Load` takto: `Parse` nebo pro podporu `Save` cesty načítání XAML, pro `Transform` podporu cesty pro uložení XAML a poskytnout techniku, která spojuje cestu zatížení a uložit cestu. `Transform`lze změnit z jednoho schématu XAML na jiné. Toto téma shrnuje každou z těchto klasifikací rozhraní API a popisuje rozdíly mezi přetížení mantinely konkrétní metody.

## <a name="load"></a>Načtení

Různá přetížení <xref:System.Xaml.XamlServices.Load%2A> implementovat úplnou logiku pro cestu zatížení. Cesta zatížení používá XAML v některých formách a výstupy datového proudu uzlu XAML. Většina těchto načítacích cest používá XAML ve formuláři kódovaného textového souboru XML. Můžete však také načíst obecný datový proud nebo můžete načíst předinstalovaný zdroj XAML, který je již obsažen v jiné <xref:System.Xaml.XamlReader> implementaci.

Nejjednodušší přetížení pro většinu <xref:System.Xaml.XamlServices.Load%28System.String%29>scénářů je . Toto přetížení `fileName` má parametr, který je jednoduše název textového souboru, který obsahuje XAML načíst. To je vhodné pro scénáře aplikace, jako je například úplné důvěryhodnosti aplikace, které mají dříve serializovaný stav nebo data do místního počítače. To je také užitečné pro architektury, kde definujete model aplikace a chcete načíst jeden ze standardních souborů, který definuje chování aplikace, spuštění uživatelského rozhraní nebo jiné funkce definované v rámci, které používají XAML.

<xref:System.Xaml.XamlServices.Load%28System.IO.Stream%29>má podobné scénáře. Toto přetížení může být užitečné, pokud máte uživatel <xref:System.IO.Stream> zvolit soubory k <xref:System.IO> načtení, protože a je častý výstup jiných rozhraní API, které mohou přistupovat k systému souborů. Nebo můžete přistupovat ke zdrojům XAML prostřednictvím asynchronních stahování nebo jiných síťových technik, které také poskytují datový proud. (Načítání z datového proudu nebo uživatelem vybraného zdroje může mít důsledky pro zabezpečení. Další informace naleznete v [tématu Aspekty zabezpečení XAML](security-considerations.md).)

<xref:System.Xaml.XamlServices.Load%28System.IO.TextReader%29>a <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> jsou přetížení, které spoléhají na čtečky formátů z předchozích verzí rozhraní .NET. Chcete-li použít tyto přetížení, měli jste již `Create` vytvořili instanci čtečky a použít jeho rozhraní API k načtení XAML v příslušném formuláři (text nebo XML). Pokud jste již přesunuli ukazatele záznamů v jiných čtecích čtecích položkách nebo s nimi provedli jiné operace, není to důležité. Logika cesty <xref:System.Xaml.XamlServices.Load%2A> načítání vždy zpracovává celý vstup XAML z kořenového adresáře. Použití těchto přetížení může vyžadovat následující scénáře:

- Návrhpovrchů, kde poskytujete jednoduchou funkci úprav XAML z existujícího textového editoru specifického pro XML.

- Varianty základních <xref:System.IO> scénářů, kde používáte vyhrazené čtečky k otevření souborů nebo datových proudů. Vaše logika provádí základní kontrolu nebo zpracování obsahu před pokusem o načtení jako XAML.

Můžete buď načíst soubor nebo datový proud, <xref:System.IO.TextReader>nebo <xref:System.Xaml.XamlReader> můžete načíst <xref:System.Xml.XmlReader>, nebo, který zabalí vstup XAML načtením pomocí souborů API čtečky.

Interně každé z předchozích přetížení je <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29>nakonec a <xref:System.Xml.XmlReader> předána slouží <xref:System.Xaml.XamlXmlReader>k vytvoření nového .

Podpis, `Load` který poskytuje pokročilejší scénáře <xref:System.Xaml.XamlServices.Load%28System.Xaml.XamlReader%29>je . Tento podpis můžete použít pro jeden z následujících případů:

- Definovali jste vlastní implementaci <xref:System.Xaml.XamlReader>.

- Je třeba zadat <xref:System.Xaml.XamlReader> nastavení, která se liší od výchozího nastavení.

Příklady nastavení, která nejsou výchozí:

<xref:System.Xaml.XamlReaderSettings.AllowProtectedMembersOnRoot%2A>\
<xref:System.Xaml.XamlReaderSettings.BaseUri%2A>\
<xref:System.Xaml.XamlReaderSettings.IgnoreUidsOnPropertyElements%2A>\
<xref:System.Xaml.XamlReaderSettings.LocalAssembly%2A>\
<xref:System.Xaml.XamlReaderSettings.ValuesMustBeString%2A>.

Výchozí čtečka <xref:System.Xaml.XamlServices> <xref:System.Xaml.XamlXmlReader>pro je . Pokud poskytnete <xref:System.Xaml.XamlXmlReader> vlastní nastavení, nastavíte nevýchozí <xref:System.Xaml.XamlXmlReaderSettings>vlastnosti:

<xref:System.Xaml.XamlXmlReaderSettings.CloseInput%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.SkipXmlCompatibilityProcessing%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlLang%2A>\
<xref:System.Xaml.XamlXmlReaderSettings.XmlSpacePreserve%2A>

## <a name="parse"></a>Analyzovat

<xref:System.Xaml.XamlServices.Parse%2A>je `Load` jako proto, že se jedná o rozhraní API načíst cestu, které vytváří datový proud uzlu XAML ze vstupu XAML. V tomto případě je však vstup XAML k dispozici přímo jako řetězec, který obsahuje všechny XAML načíst. <xref:System.Xaml.XamlServices.Parse%2A>je zjednodušený přístup, který je vhodnější pro scénáře aplikace než scénáře architektury. Další informace naleznete v tématu <xref:System.Xaml.XamlServices.Parse%2A>. <xref:System.Xaml.XamlServices.Parse%2A>je pouze zabalené <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29> volání, <xref:System.IO.StringReader> které zahrnuje interně.

## <a name="save"></a>Uložit

Různé přetížení <xref:System.Xaml.XamlServices.Save%2A> implementovat cestu uložit. <xref:System.Xaml.XamlServices.Save%2A> Všechny metody všechny vzít objekt graf jako vstup a vytvořit výstup <xref:System.Xml.XmlWriter> / <xref:System.IO.TextWriter> jako datový proud, soubor nebo instance.

Očekává se, že vstupní objekt bude kořenovým objektem některých reprezentací objektu. Může se jedná o jeden kořen obchodního objektu, kořen stromu objektů pro stránku ve scénáři ui, pracovní editační povrch z návrhového nástroje nebo jiné koncepty kořenových objektů, které jsou vhodné pro scénáře.

V mnoha scénářích strom objektů, který uložíte, souvisí s <xref:System.Xaml.XamlServices.Load%2A> původní operací, která načetla XAML s jiným rozhraním API implementovaným modelem architektury nebo aplikace. Mohou existovat rozdíly zachycené ve stromu objektů, které jsou způsobeny změnami stavu, změnami, kdy vaše aplikace zachytila nastavení běhu od uživatele, změnila XAML, protože vaše aplikace je návrhová plocha XAML atd. Se změnami nebo bez změny, koncept první načítání XAML ze značky a potom znovu uložit a porovnání dvou xaml značkovací formuláře je někdy označovánjako round-trip reprezentace XAML.

Výzvou s ukládáním a serializací složitého objektu, který je nastaven ve formuláři značek, je dosažení rovnováhy mezi úplnou reprezentací bez ztráty informací a podrobností, která činí XAML méně čitelným pro člověka. Kromě toho mohou mít různí zákazníci pro XAML různé definice nebo očekávání, jak by měla být tato rovnováha nastavena. Api <xref:System.Xaml.XamlServices.Save%2A> představují jednu definici této rovnováhy. Rozhraní <xref:System.Xaml.XamlServices.Save%2A> API používají k dispozici kontext schématu XAML a výchozí <xref:System.Xaml.XamlType> <xref:System.Xaml.XamlMember>charakteristiky založené na CLR , a další koncepty vnitřního systému XAML a xaml k určení, kde lze optimalizovat určité konstrukce datového proudu uzlů XAML, když jsou uloženy zpět do značek. Například <xref:System.Xaml.XamlServices> uložit cesty můžete použít clr výchozí xaml schéma kontextu <xref:System.Xaml.XamlType> vyřešit pro <xref:System.Xaml.XamlType.ContentProperty%2A?displayProperty=nameWithType>objekty, můžete určit , a pak můžete vynechat tagy prvku vlastnosti při zápisu vlastnosti do obsahu XAML objektu.

<a name="transform"></a>
## <a name="transform"></a>Transformace

<xref:System.Xaml.XamlServices.Transform%2A>převádí nebo transformuje XAML propojením cesty načítání a cesty pro uložení jako jedné operace. Jiný kontext schématu nebo jiný systém typu zálohování <xref:System.Xaml.XamlReader> <xref:System.Xaml.XamlWriter>lze použít pro a , což je, co ovlivňuje způsob transformace výsledné xaml. To funguje dobře pro operace s širokou transformací.

Pro operace, které spoléhají na zkoumání každého uzlu v datovém proudu uzlu <xref:System.Xaml.XamlServices.Transform%2A>XAML, obvykle nepoužíváte . Místo toho je třeba definovat vlastní zatížení cesta uložit cestu operace řady a interject vlastní logiku. V jedné z cest použijte dvojici zapisovače XAML/XAML kolem smyčky vlastního uzlu. Například načíst počáteční XAML pomocí <xref:System.Xaml.XamlXmlReader> a krok <xref:System.Xaml.XamlXmlReader.Read%2A> do uzlů s po sobě jdoucích volání. Provoz na úrovni datového proudu uzlu XAML můžete nyní upravit jednotlivé uzly (typy, členy, jiné uzly) použít transformaci nebo ponechat uzel tak, jak je. Potom odešlete uzel dále do `Write` příslušného <xref:System.Xaml.XamlObjectWriter> rozhraní API a zapíšete objekt. Další informace naleznete [v tématu Principy struktury a koncepty datových proudů uzlů XAML](understanding-xaml-node-stream-structures-and-concepts.md).

## <a name="see-also"></a>Viz také

- <xref:System.Xaml.XamlObjectWriter>
- <xref:System.Xaml.XamlServices>
- [XAML Services](../../../api/index.md)
