---
title: Obory názvů XAML pro služby .NET XAML
ms.date: 03/30/2017
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
ms.openlocfilehash: 2ae57d08fade85c59fea2a54b653a2f775b57415
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071841"
---
# <a name="xaml-namespaces-for-net-xaml-services"></a>Obory názvů XAML pro služby .NET XAML
Obor názvů XAML je koncept, který rozšiřuje definici oboru názvů XML. Podobně jako v oboru názvů XML můžete definovat obor `xmlns` názvů XAML pomocí atributu ve značkách. Obory názvů XAML jsou také reprezentovány v datovém proudu uzlů XAML a dalších api služeb XAML. Toto téma definuje koncept oboru názvů XAML a popisuje, jak lze definovat obory názvů XAML a jak je používají kontexty schématu XAML a další aspekty služby .NET XAML Services.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Obor názvů XML a Obor názvů XAML  
 Obor názvů XAML je specializovaný obor názvů XML, stejně jako XAML je specializovaná forma xml a používá základní formulář XML pro své značky. Ve značkování deklarujete obor názvů XAML a jeho mapování pomocí atributu `xmlns` použitého na prvek. Deklarace `xmlns` může být provedena na stejný prvek, který xaml obor názvů je deklarován v. Deklarace oboru názvů XAML provedená prvku je platná pro tento prvek, všechny atributy tohoto prvku a všechny podřízené objekty tohoto prvku. Atributy mohou používat obor názvů XAML, který není stejný jako prvek, který obsahuje atribut, pokud samotný název atributu odkazuje na předponu jako součást názvu atributu ve značkách.  
  
 Obor názvů XAML a obor názvů XML je rozdíl, že obor názvů XML může být použit k odkazování na schéma nebo jednoduše k rozlišení entit. Pro XAML typy a členy používané v XAML musí být nakonec vyřešeny na záložní typy a koncepty schématu XML se na tuto schopnost nevztahují dobře. Obor názvů XAML obsahuje informace, které musí mít k dispozici kontext schématu XAML, aby bylo možné provést toto mapování typů.  
  
## <a name="xaml-namespace-components"></a>Součásti oboru názvů XAML  
 Definice oboru názvů XAML má dvě součásti: předponu a identifikátor. Každá z těchto součástí je k dispozici, když je ve značkách deklarován obor názvů XAML nebo definován v systému typu XAML.  
  
 Předpona může být libovolný řetězec, jak je povoleno [W3C Namespaces ve specifikaci XML 1.0](https://www.w3.org/TR/REC-xml-names/). Podle konvence jsou předpony obvykle krátké řetězce, protože předpona se opakuje mnohokrát v typickém souboru značek. Některé obory názvů XAML, které jsou určeny k použití ve více implementacích XAML, používají konkrétní konvenční předpony. Například obor názvů XAML jazyka XAML je obvykle mapován pomocí předpony `x`. Můžete definovat výchozí obor názvů XAML, kde předpona není uvedena v definici, ale je reprezentována jako prázdný řetězec, pokud je definován nebo dotazován by.NET rozhraní API služby XAML. Výchozí obor názvů XAML je obvykle záměrně vybrán, aby se podpořilo maximální množství značek, které vynechují předponu, technologií implementující XAML a jejími scénáři a slovníky.  
  
 Identifikátor může být libovolný řetězec, jak je povoleno [W3C Namespaces ve specifikaci XML 1.0](https://www.w3.org/TR/REC-xml-names/). Podle konvence jsou identifikátory pro obory názvů XML nebo obory názvů XAML často uvedeny ve formuláři URI, obvykle jako absolutní identifikátor URI s kvalifikací protokolu. Informace o verzi, která definuje konkrétní slovník XAML je implicitní jako součást řetězce cesty. Obory názvů XAML přidávají další konvenci identifikátorů nad rámec konvence IDENTIFIKÁTOR XML. Pro obory názvů XAML identifikátor sděluje informace, které je potřeba kontext schématu XAML k vyřešení typy, které jsou určeny jako prvky v rámci tohoto oboru názvů XAML nebo přeložit atributy členům.  
  
 Pro účely sdělování informací kontextu schématu XAML může být identifikátor oboru názvů XAML stále ve formě identifikátoru URI. V tomto případě je však identifikátor URI také deklarován jako odpovídající identifikátor v určitém sestavení nebo seznamu sestavení. To se provádí v sestaveních přiřazením sestavení s <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Tato metoda identifikace oboru názvů XAML a podpora chování překladu typu založeného na CLR v přiděleném sestavení je podporována výchozím kontextem schématu XAML ve službě .NET XAML Services. Obecněji lze tuto konvenci použít pro případy, kdy kontext schématu XAML zahrnuje clr nebo je založen na výchozí kontext schématu XAML, který je nezbytný pro čtení atributů CLR ze sestavení CLR.  
  
 Obory názvů XAML lze také identifikovat podle konvence, která komunikuje obor názvů CLR a sestavení definující typ. Tato konvence se používá <xref:System.Windows.Markup.XmlnsDefinitionAttribute> v případech, kdy neexistuje žádné přiřazení v sestaveních, které obsahují typy. Tato konvence je potenciálně složitější než konvence URI a má také potenciál pro nejednoznačnost a duplikaci, protože existuje několik způsobů, jak odkazovat na sestavení.  
  
 Nejzákladnější forma identifikátoru, který používá obor názvů CLR a konvence sestavení, je následující:  
  
 `clr-namespace:clrnsName; assembly=assemblyShortName`
  
 `clr-namespace:`a `; assembly=` jsou doslovné součásti syntaxe.  
  
 *clrnsName* je název řetězce, který identifikuje obor názvů CLR. Tento název řetězce obsahuje všechny vnitřní tečky znaky (.), které poskytují rady o oboru názvů CLR a jeho vztah k jiným oborům názvů CLR.
  
 *assemblyShortName* je název řetězce sestavení, který definuje typy, které jsou užitečné v XAML. Očekává se, že typy, ke kterým bude přístup n. c) prostřednictvím deklarovaného oboru názvů XAML, budou definovány sestavením a budou deklarovány v rámci oboru názvů CLR určeného *clrnsName*. Tento název řetězce obvykle paralely informace, jak je uvedeno . <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>  
  
 Úplnější definice oboru názvů CLR a konvence sestavení je následující:  
  
 `clr-namespace:clrnsName; assembly=assemblyName`
  
 *assemblyName* představuje libovolný řetězec, <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> který je legální jako vstup. Tento řetězec může obsahovat informace o jazykové verzi, veřejném klíči nebo verzi <xref:System.Reflection.Assembly>(definice těchto konceptů jsou definovány v referenčním tématu pro). Formát COFF a důkazy (používané jinými přetíženími) <xref:System.Reflection.Assembly.Load%2A>nejsou relevantní pro účely zatížení sestavy XAML; všechny informace o zatížení musí být prezentovány jako řetězec.  
  
 Určení veřejného klíče pro sestavení je užitečná technika pro zabezpečení XAML nebo pro odstranění možné nejednoznačnosti, která může existovat, pokud jsou sestavení načtena jednoduchým názvem nebo existují předem v mezipaměti nebo doméně aplikace. Další informace naleznete v [tématu Aspekty zabezpečení XAML](security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Deklarace oboru názvů XAML v rozhraní API služby XAML  
 V rozhraní API služby XAML je deklarace oboru <xref:System.Xaml.NamespaceDeclaration> názvů XAML reprezentována objektem. Pokud deklarujete obor názvů XAML <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> v kódu, zavoláte konstruktor. `ns` Parametry `prefix` a jsou určeny jako řetězce a vstup pro poskytnutí těchto parametrů odpovídá definici identifikátoru oboru názvů XAML a předpony oboru názvů XAML, jak je uvedeno dříve v tomto tématu.  
  
 Pokud zkoumáte informace o oboru názvů XAML jako součást datového proudu uzlu XAML nebo <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> prostřednictvím jiného přístupu <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> k systému typu XAML, hlásí identifikátor oboru názvů XAML a hlásí předponu oboru názvů XAML.  
  
 V datovém proudu uzlu XAML se informace o oboru názvů XAML mohou zobrazit jako uzel XAML, který předchází entitě, na kterou se vztahuje. To zahrnuje případy, kdy informace o oboru `StartObject` názvů XAML předchází kořenový prvek XAML. Další informace naleznete [v tématu Principy struktury a koncepty datových proudů uzlů XAML](understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Pro mnoho scénářů, které používají rozhraní API služby .NET XAML, se očekává, že existuje alespoň jedna deklarace oboru názvů XAML a deklarace musí obsahovat nebo odkazovat na informace, které jsou vyžadovány kontextem schématu XAML. Obory názvů XAML musí buď zadat sestavení, která mají být načtena, nebo pomoci při řešení určitých typů v oborech názvů a sestaveních, které jsou již načteny nebo známy kontextem schématu XAML.  
  
 Aby bylo možné generovat datový proud uzlu XAML, musí být k dispozici informace o typu XAML prostřednictvím kontextu schématu XAML. Informace o typu XAML nelze určit bez prvního určení příslušného oboru názvů XAML pro každý uzel, který má být vytvořit. V tomto okamžiku jsou zatím vytvořeny žádné instance typů, ale kontext schématu XAML může být nutné vyhledat informace z definující sestavení a typ zálohování. Chcete-li například zpracovat `<Party><PartyFavor/></Party>`značky , musí být kontext schématu XAML schopen určit `ContentProperty` `Party`název a typ of , a proto `Party` musí `PartyFavor`také znát informace o oboru názvů XAML pro a . V případě výchozího kontextu schématu XAML hlásí statický odraz většinu informací o systému typu XAML, které jsou potřebné ke generování uzlů typu XAML v datovém proudu uzlu.  
  
 Aby bylo možné generovat objektový graf z datového proudu uzlu XAML, musí existovat deklarace oboru názvů XAML pro každou předponu XAML použitou v původní značce a zaznamenanou v datovém proudu uzlu XAML. V tomto okamžiku jsou vytvářeny instance a true chování mapování typu dochází.  
  
 Pokud potřebujete předem vyplnit informace o oboru názvů XAML, není v kódu definován obor názvů XAML, který chcete použít v kontextu schématu XAML, je <xref:System.Xml.XmlParserContext> jedna <xref:System.Xml.XmlReader>technika, kterou můžete použít, deklarovat deklarace oboru názvů XML v aplikaci . Pak použijte <xref:System.Xml.XmlReader> jako vstup pro konstruktor čtečky <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>XAML, nebo .  
  
 Dvě další rozhraní API, která jsou relevantní pro zpracování oboru názvů XAML ve službě .NET XAML Services, jsou atributy <xref:System.Windows.Markup.XmlnsDefinitionAttribute> a <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Tyto atributy platí pro sestavení. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>používá kontext schématu XAML k interpretaci jakékoli deklarace oboru názvů XAML, která obsahuje identifikátor URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute>používá nástroje, které vyzařují XAML tak, aby konkrétní obor názvů XAML lze serializovat s předvídatelnou předponou. Další informace naleznete [v tématu Atributy CLR související s XAML pro vlastní typy a knihovny](clr-attributes-with-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Viz také

- [Principy struktur a koncepcí datových proudů uzlů XAML](understanding-xaml-node-stream-structures-and-concepts.md)
