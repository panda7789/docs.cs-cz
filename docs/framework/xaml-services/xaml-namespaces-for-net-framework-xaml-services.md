---
title: Obory názvů jazyka XAML pro technologii .NET Framework XAML Services
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 2e9e2d9e2257e5e6059210b82a69d7a837254032
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54736796"
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Obory názvů jazyka XAML pro technologii .NET Framework XAML Services
Obor názvů XAML je pojem, který rozšiřuje definici oboru názvů XML. Podobně jako obor názvů XML, můžete definovat obor názvů XAML pomocí `xmlns` atribut v kódu. Obory názvů XAML jsou také reprezentované v datovém proudu uzlu XAML a jiných rozhraní API služeb XAML. Toto téma definuje pojem oboru názvů XAML a popisuje, jak lze definovat obory názvů XAML a jsou používány kontext schématu XAML a další aspekty rozhraní .NET Framework XAML Services.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Namespace XML a Namespace XAML  
 Obor názvů XAML je specializované oboru názvů XML, stejně jako XAML je specializovaná forma XML a používá základní formulář XML pro jeho značky. Ve značce, deklarujte obor názvů XAML a jeho mapování prostřednictvím `xmlns` atribut použitá pro element. `xmlns` Prohlášení stejného elementu, který je deklarován obor názvů XAML v. Deklarace oboru názvů XAML provedené na prvek je platný pro tento element, všechny atributy daného prvku a všechny podřízené objekty daného prvku. Obory názvů XAML, který není stejný jako prvek, který obsahuje atribut, tak dlouho, dokud odkazuje samotný název atributu předponu jako součást názvu atributu v kódu můžete použít atributy.  
  
 Rozlišení oboru názvů XAML a obor názvů XML je, že obor názvů XML může slouží k odkazování schéma nebo mohou sloužit k rozlišení jednoduše entity. Pro XAML typy a členy v XAML musí nakonec přeložit na typy zálohování a koncepty schématu XML se nedá použít také k této funkci. Obor názvů XAML obsahuje informace, že kontext schématu XAML musí mít k dispozici, aby bylo možné provést toto mapování typu.  
  
## <a name="xaml-namespace-components"></a>Součásti Namespace XAML  
 Definice oboru názvů XAML má dvě součásti: předponu a identifikátor. Každá z těchto komponent jsou k dispozici, pokud obor názvů XAML je deklarována v kódu nebo definovaných v typu systému XAML.  
  
 Předpona, která může být libovolný řetězec, to povoluje [názvových prostorech W3C XML 1.0 – specifikace](https://go.microsoft.com/fwlink/?LinkID=161735) . Podle konvence předpony jsou obvykle velmi krátké řetězce, protože předpona, která se opakuje tolikrát, kolikrát v souboru typické označení. Některé obory názvů XAML, které jsou určeny pro použití ve více implementací XAML používat konkrétní konvenční předpony. Například XAML jazyka XAML je mapovaný obor názvů obvykle pomocí předpony `x`. Můžete definovat výchozí XAML oboru názvů, kde není uveden v definici předponu, ale je vyjádřena jako prázdný řetězec, je-li definována nebo dotazovat by.NET Framework XAML Services API. Obvykle je výchozí obor názvů XAML záměrně vybrán aby podpořilo maximalizované množství vynechání předponu značky XAML implementace technologie a scénáře a vocabularies.  
  
 Identifikátor může být libovolný řetězec, to povoluje [názvových prostorech W3C XML 1.0 – specifikace](https://go.microsoft.com/fwlink/?LinkID=161735). Podle konvence identifikátory pro obory názvů XML nebo XAML obory názvů často disponují v podobě identifikátoru URI, obvykle jako protokolu kvalifikovaný absolutní identifikátor URI. Informace o verzi, která definuje určité slovníkové XAML je často vyjádřena jako součást řetězec cesty. Obory názvů XAML, přidejte vytváření další identifikátor nad rámec konvence URI v kódu XML. Pro obory názvů XAML komunikuje tento identifikátor informace, které je potřeba kontext schématu XAML pro překlad typů, které jsou určené jako prvky v tomto oboru názvů XAML, nebo pokud chcete vyřešit atributy na členy.  
  
 Pro účely předávání informací na kontext schématu XAML identifikátor pro obor názvů XAML může být stále v podobě identifikátoru URI. Ale v tomto případě identifikátor URI je také deklarován jako odpovídající identifikátor v konkrétní sestavení nebo seznam sestavení. To se provádí v sestaveních přidělování sestavení s <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Výchozí kontext schématu XAML v rozhraní .NET Framework XAML Services podporuje tuto metodu identifikaci oboru názvů XAML a podporuje chování překladu typu založeného na modulu CLR v sestavení s atributy. Obecně platí je možné tato konvence pro případy, kdy kontext schématu XAML zahrnuje modul CLR nebo je založena na výchozí kontext schématu XAML, což je nezbytné, aby bylo možné číst atributy CLR ze sestavení CLR.  
  
 Obory názvů XAML lze také identifikovat konvencí komunikující obor názvů CLR na typ definice sestavení. Tato úmluva se používá v případech, kdy ne <xref:System.Windows.Markup.XmlnsDefinitionAttribute> attribution existuje v sestavení, které obsahují typy. Tato konvence je potenciálně složitější než zápisu identifikátoru URI a také má potenciál pro nejednoznačnosti a duplikování, protože existuje více způsobů odkazů na sestavení.  
  
 Většina základních formu identifikátor, který používá konvence oboru názvů a sestavení CLR je následujícím způsobem:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:` a `; assembly=` jsou literálu součásti syntaxe.  
  
 *clrnsName* je název řetězce, který identifikuje obor názvů CLR. Tento řetězec názvu obsahuje znaky interní tečka (.), které poskytnout nápovědu, obor názvů CLR a jejich vztah k jiné oborů názvů CLR.  
  
 *assemblyShortName* je název řetězce objektu sestavení, který definuje typy, které jsou užitečné v XAML. Typy přístup prostřednictvím oboru názvů deklarovaný XAML se očekává a podle sestavení speciálně deklarovat v rámci určeného oboru názvů CLR *clrnsName*. Tento název řetězce obvykle parallels informace, jak je hlásí <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Kompletní definici konvence oboru názvů a sestavení CLR je následujícím způsobem:  
  
 `clr-namespace:` *clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* představuje libovolný řetězec, který je platný jako <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> vstupu. Tento řetězec může obsahovat jazykové verze, veřejného klíče nebo informace o verzi (definice těchto konceptů, které jsou definovány v referenčním tématu pro <xref:System.Reflection.Assembly>). COFF formátu a důkazy (jako další přetížení <xref:System.Reflection.Assembly.Load%2A>) nejsou relevantní pro načítání účely; sestavení XAML všechny informace o načtení musí být uvedené jako řetězec.  
  
 Zadáte veřejný klíč pro sestavení je užitečná technika XAML zabezpečení nebo pro odebrání možné nejednoznačnost, která mohou existovat, pokud se načetl jednoduchý název sestavení nebo existovat v doméně mezipaměti nebo aplikace. Další informace najdete v tématu [aspekty zabezpečení XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Deklarace Namespace XAML v rozhraní API služeb XAML  
 V rozhraní API služby XAML je reprezentována deklarace oboru názvů XAML <xref:System.Xaml.NamespaceDeclaration> objektu. Pokud se deklarace oboru názvů XAML v kódu, můžete volat <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> konstruktoru. `ns` a `prefix` parametry jsou zadané jako řetězce a vstup k poskytování těchto parametrů odpovídá definici identifikátor oboru názvů XAML a předponu oboru názvů XAML uvedené dříve v tomto tématu.  
  
 Pokud zkoumáte informace oboru názvů XAML jako součást datový proud uzlu XAML nebo prostřednictvím jiný přístup k typu systému XAML <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> sestavy identifikátor oboru názvů XAML a <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> sestavy předponu oboru názvů XAML.  
  
 V datovém proudu uzlu XAML informace oboru názvů XAML zobrazit jako uzel XAML, který předchází entit, ke kterému se vztahuje. To zahrnuje případy, kdy předchází informace oboru názvů XAML `StartObject` pro daný kořenový prvek XAML. Další informace najdete v tématu [Principy XAML Stream struktur a koncepcí uzlů](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Pro většinu scénářů, které používají rozhraní .NET Framework XAML Services API nejmíň jednu deklaraci oboru názvů XAML je se očekával a deklarace musí obsahovat nebo o informace, které vyžaduje kontext schématu XAML. Obory názvů XAML musí zadat sestavení, které může být načteny, nebo pomáhají při řešení konkrétních typů v rámci obory názvů a sestavení, která jsou už načteny nebo nezná kontext schématu XAML.  
  
 Aby bylo možné generovat datový proud uzlu XAML, musí být k dispozici prostřednictvím kontext schématu XAML informace o typu XAML. Informace o typu XAML nelze určit bez první zjišťování relevantní oboru názvů XAML pro každý uzel k vytvoření. V tomto okamžiku se zatím nevytvořili žádné instance typů, ale kontext schématu XAML může potřebovat vyhledat informace z definice sestavení a typ zálohování. Například, aby bylo možné zpracovat značky `<Party><PartyFavor/></Party>`, kontext schématu XAML musí být schopní určit název a typ `ContentProperty` z `Party`a proto taky musíte znát informace oboru názvů XAML pro `Party` a `PartyFavor`. V případě výchozí kontext schématu XAML sestavy statické reflexe většinu informací typu systému XAML, které je nutné pro vygenerování typů uzlů XAML v datovém proudu uzlu.  
  
 Aby bylo možné generovat grafu objektů z datový proud uzlu XAML, musí existovat deklarace oboru názvů XAML pro každou předponu XAML používají v původní kód a zaznamenaná v datovém proudu uzlu XAML. V tuto chvíli Probíhá vytváření instancí a true mapování typu chování.  
  
 Potřebujete předvyplní informace oboru názvů XAML, v případech, kde máte v úmyslu kontext schématu XAML používat obor názvů XAML není definovaný v kódu, je jednou z metod můžete použít k deklarování deklarace oboru názvů XML v <xref:System.Xml.XmlParserContext> pro <xref:System.Xml.XmlReader>. Potom používat <xref:System.Xml.XmlReader> jako vstup pro konstruktor čtečky XAML nebo <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Dva další rozhraní API, které jsou relevantní pro obor názvů XAML v rozhraní .NET Framework XAML Services jsou atributy <xref:System.Windows.Markup.XmlnsDefinitionAttribute> a <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Tyto atributy se vztahují na sestavení. <xref:System.Windows.Markup.XmlnsDefinitionAttribute> používá kontext schématu XAML pro interpretaci všechny deklarace oboru názvů XAML, která obsahuje identifikátor URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute> používá nástroje, které generují XAML tak, aby konkrétní obor názvů XAML lze serializovat s příznakem předponu předvídatelné. Další informace najdete v tématu [XAML-Related CLR atributy pro vlastní typy a knihovny](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Viz také:
- [Principy struktur a koncepcí streamu uzlů XAML](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
