---
title: Obory názvů jazyka XAML pro technologii .NET Framework XAML Services
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 11bf5d112c64fb0b942decf7635f02b90a98bdeb
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837165"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Obory názvů jazyka XAML pro technologii .NET Framework XAML Services
Obor názvů XAML je koncept, který se rozbalí do definice oboru názvů XML. Podobně jako obor názvů XML, můžete definovat obor názvů XAML pomocí atributu `xmlns` v kódu. Obory názvů XAML jsou také zastoupeny v datovém proudu uzlu XAML a v dalších rozhraních API služeb XAML. Toto téma definuje koncept oboru názvů XAML a popisuje, jak lze definovat obory názvů XAML a jsou používány kontexty schématu XAML a dalšími aspekty .NET Frameworkch služeb XAML.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Obor názvů XML a obor názvů XAML  
 Obor názvů XAML je specializovaný obor názvů XML, stejně jako XAML je specializované formuláře XML a používá základní formulář XML pro svůj kód. V kódu deklarujete obor názvů XAML a jeho mapování pomocí atributu `xmlns` použitého pro element. Deklaraci `xmlns` lze provést u stejného prvku, v němž je deklarován obor názvů XAML. Deklarace oboru názvů XAML vytvořená pro element je platná pro tento element, všechny atributy tohoto prvku a všechny podřízené prvky tohoto prvku. Atributy mohou používat obory názvů XAML, které nejsou stejné jako u prvku, který obsahuje atribut, pokud název atributu sám odkazuje na předponu jako součást názvu atributu v kódu.  
  
 Rozlišení oboru názvů XAML oproti oboru názvů XML je, že obor názvů XML lze použít k odkazování na schéma, nebo může být použit k pouhému odlišení entit. V jazyce XAML musí být typy a členy, jak je použit v jazyce XAML, nakonec přeloženy na typy zálohování a koncepty schémat XML se pro tuto funkci nevztahují. Obor názvů XAML obsahuje informace, které musí mít kontext schématu XAML k dispozici, aby bylo možné provést toto mapování typu.  
  
## <a name="xaml-namespace-components"></a>Komponenty oboru názvů XAML  
 Definice oboru názvů XAML má dvě komponenty: předponu a identifikátor. Každá z těchto komponent je přítomna v případě, že je obor názvů XAML deklarován v kódu nebo je definován v systému typů XAML.  
  
 Předpona může být libovolný řetězec, který je povolený [obory názvů W3C ve specifikaci XML 1,0](https://www.w3.org/TR/REC-xml-names/) . Podle konvence jsou předpony obvykle velmi krátké řetězce, protože předpona je opakována mnohokrát v typickém souboru označení. Některé obory názvů jazyka XAML, které jsou určeny pro použití v několika implementacích jazyka XAML, používají konkrétní konvenční předpony. Například obor názvů XAML jazyka XAML je obvykle namapován pomocí `x`předpony. Můžete definovat výchozí obor názvů XAML, kde Předpona není uvedena v definici, ale je reprezentována jako prázdný řetězec, pokud je definováno nebo dotazované rozhraní API služby by.NET Framework XAML Services. Výchozí obor názvů XAML je obvykle záměrně vybrán pro zvýšení úrovně maximalizovaného kódu, který je vynechán, pomocí technologie implementující XAML a jeho scénářů a slovníků.  
  
 Identifikátor může být libovolný řetězec, který je povolený [obory názvů W3C ve specifikaci XML 1,0](https://www.w3.org/TR/REC-xml-names/). Podle konvence jsou identifikátory pro obory názvů XML nebo XAML často předány ve formě identifikátoru URI, obvykle jako absolutní identifikátor URI kvalifikovaný pro protokol. Často jsou informace o verzi definující konkrétní slovníky XAML odvozeny jako součást řetězce cesty. Obory názvů XAML přidejte další konvenci identifikátoru za rámec konvence identifikátoru URI XML. Pro obory názvů XAML identifikátor komunikuje informace, které jsou vyžadovány kontextem schématu XAML, aby bylo možné přeložit typy, které jsou zadány jako elementy v daném oboru názvů XAML, nebo pro řešení atributů na členy.  
  
 Pro účely sdělování informací do kontextu schématu XAML může být identifikátor oboru názvů XAML stále ve formátu identifikátoru URI. Nicméně v tomto případě je identifikátor URI deklarován také jako shodný identifikátor v konkrétním sestavení nebo seznamu sestavení. To se provádí v sestaveních, které připisují sestavení pomocí <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Tato metoda identifikace oboru názvů XAML a podpora chování rozlišení typů založeného na CLR v sestavení s atributy je podporována výchozím kontextem schématu XAML v .NET Framework služby XAML. Obecně platí, že tato konvence je možné použít pro případy, kdy kontext schématu XAML obsahuje CLR nebo je založen na výchozím kontextu schématu XAML, který je nezbytný pro čtení atributů CLR ze sestavení CLR.  
  
 Obory názvů XAML lze také identifikovat pomocí konvence, která komunikuje s oborem názvů CLR a sestavením definujícím typ. Tato konvence se používá v případech, kdy neexistuje žádná <xref:System.Windows.Markup.XmlnsDefinitionAttribute> označení v sestaveních, která obsahují typy. Tato konvence je potenciálně složitější než konvence identifikátoru URI a zároveň má potenciál na nejednoznačnost a duplicity, protože existuje více způsobů, jak odkazovat na sestavení.  
  
 Nejzákladnější forma identifikátoru, který používá obor názvů CLR a konvenci sestavení, je následující:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` a `; assembly=` jsou komponenty literálů syntaxe.  
  
 *clrnsName* je název řetězce, který identifikuje obor názvů CLR. Tento název řetězce obsahuje všechny znaky interních teček (.), které poskytují nápovědu k oboru názvů CLR a jeho vztah k jiným oborům názvů CLR.  
  
 *assemblyShortName* je název řetězce sestavení definující typy, které jsou užitečné v jazyce XAML. Je očekáváno, že typy, které mají být získány prostřednictvím deklarovaného oboru názvů XAML, definovány sestavením a jsou výslovně deklarovány v rámci oboru názvů CLR určeného parametrem *clrnsName*. Tento název řetězce obvykle paralelismus informace, jak je uvedeno <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Úplnější definice oboru názvů CLR a konvence sestavení jsou následující:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *AssemblyName*  
  
 *AssemblyName* představuje libovolný řetězec, který je platný jako vstup <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType>. Tento řetězec může obsahovat informace o jazykové verzi, veřejném klíči nebo verzi (definice těchto konceptů jsou definovány v referenčním tématu pro <xref:System.Reflection.Assembly>). Formát COFF a legitimace (jak je používá jiné přetížení <xref:System.Reflection.Assembly.Load%2A>) nejsou relevantní pro účely načítání sestavení XAML. všechny informace o načítání musí být uvedeny jako řetězec.  
  
 Zadání veřejného klíče pro sestavení je užitečnou technikou pro zabezpečení XAML nebo pro odstranění možné nejednoznačnosti, která může existovat, pokud jsou sestavení načítána pomocí jednoduchého názvu nebo v mezipaměti nebo doméně aplikace. Další informace najdete v tématu věnovaném [hlediskům zabezpečení XAML](xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Deklarace oboru názvů XAML v rozhraní API služby XAML  
 V rozhraní API služeb XAML je deklarace oboru názvů XAML reprezentována objektem <xref:System.Xaml.NamespaceDeclaration>. Pokud deklarujete obor názvů XAML v kódu, zavoláte konstruktor <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29>. Parametry `ns` a `prefix` jsou zadány jako řetězce a zadání pro tyto parametry odpovídá definici identifikátoru oboru názvů XAML a předpony oboru názvů jazyka XAML, jak je uvedeno dříve v tomto tématu.  
  
 Pokud zkoumáte informace oboru názvů XAML jako součást datového proudu uzlu XAML nebo prostřednictvím jiného přístupu k systému typů XAML, <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> nahlásí identifikátor oboru názvů XAML a <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> vypíše předponu oboru názvů XAML.  
  
 V datovém proudu uzlu XAML se mohou informace o oboru názvů XAML zobrazit jako uzel XAML, který předchází entitě, na kterou se vztahuje. To zahrnuje případy, kdy informace oboru názvů XAML předchází `StartObject` kořenového prvku jazyka XAML. Další informace najdete v tématu [Principy struktur a konceptů datového proudu uzlu XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Pro mnoho scénářů, které používají .NET Framework rozhraní API služby XAML, musí existovat alespoň jedna deklarace oboru názvů jazyka XAML a deklarace musí buď obsahovat, nebo odkazovat na informace, které jsou vyžadovány kontextem schématu XAML. Obory názvů XAML musí buď určovat sestavení, která mají být načtena, nebo pomáhat při řešení specifických typů v oborech názvů a sestaveních, které jsou již načteny nebo známy v kontextu schématu XAML.  
  
 Aby bylo možné generovat datový proud uzlu XAML, musí být k dispozici informace o typu XAML prostřednictvím kontextu schématu XAML. Informace o typu XAML nelze určit bez prvotního určení odpovídajícího oboru názvů XAML pro každý uzel, který chcete vytvořit. V tomto okamžiku nejsou ještě vytvořeny žádné instance typů, ale kontext schématu XAML může potřebovat vyhledat informace z definujícího sestavení a typu zálohování. Například pro zpracování `<Party><PartyFavor/></Party>`značek musí být kontext schématu XAML schopný určit název a typ `ContentProperty` `Party`, a tak musí také znát informace oboru názvů XAML pro `Party` a `PartyFavor`. V případě výchozího kontextu schématu XAML, statické reflexe sestaví většinu systémových informací typu XAML, které jsou potřebné pro generování uzlů typu XAML v proudu uzlů.  
  
 Aby bylo možné generovat graf objektů z datového proudu uzlu XAML, musí existovat deklarace oboru názvů XAML pro každou předponu XAML použitou v původním kódu a zaznamenanou v datovém proudu uzlu XAML. V tomto okamžiku jsou vytvářeny instance a dojde k chování mapování typu true.  
  
 Pokud potřebujete předem naplnit informace oboru názvů XAML, v případech, kdy se obor názvů XAML, který chcete použít pro použití kontextu schématu XAML, nedefinuje v kódu, jedna technika, kterou můžete použít, je deklarovat deklarace oboru názvů XML v <xref:System.Xml.XmlParserContext> pro <xref:System.Xml.XmlReader>. Pak použijte tento <xref:System.Xml.XmlReader> jako vstup pro konstruktor čtečky XAML nebo <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Druhé rozhraní API, které je relevantní pro zpracování oboru názvů XAML v .NET Framework služby XAML, jsou atributy <xref:System.Windows.Markup.XmlnsDefinitionAttribute> a <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Tyto atributy se vztahují na sestavení. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> používá kontext schématu XAML k interpretaci jakékoli deklarace oboru názvů XAML, která obsahuje identifikátor URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute> jsou používány pomocí nástrojů, které generují XAML tak, aby určitý obor názvů XAML mohl být serializován s předvídatelné předponou. Další informace naleznete v tématu [atributy CLR související s jazykem XAML pro vlastní typy a knihovny](xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Viz také:

- [Principy struktur a koncepcí streamu uzlů XAML](understanding-xaml-node-stream-structures-and-concepts.md)
