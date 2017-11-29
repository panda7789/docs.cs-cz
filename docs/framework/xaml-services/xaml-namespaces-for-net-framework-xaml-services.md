---
title: "Obory názvů jazyka XAML pro technologii .NET Framework XAML Services"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e4f15f13-c420-4c1e-aeab-9b6f50212047
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: e09279209bf3d6925b61d55d6988b5af658f5aab
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="xaml-namespaces-for-net-framework-xaml-services"></a>Obory názvů jazyka XAML pro technologii .NET Framework XAML Services
Oboru názvů jazyka XAML je konceptu, které rozšíří na definici oboru názvů XML. Podobně jako u oboru názvů XML, můžete definovat pomocí oboru názvů jazyka XAML `xmlns` atribut v kódu. Obory názvů jazyka XAML jsou také reprezentované v datový proud uzlu XAML a jiná rozhraní API služby XAML. Toto téma definuje koncept oboru názvů jazyka XAML a popisuje, jak lze definovat obory názvů jazyka XAML a jsou používány kontexty schématu XAML a dalších aspektů rozhraní .NET Framework XAML Services.  
  
## <a name="xml-namespace-and-xaml-namespace"></a>Namespace XML a Namespace XAML  
 Oboru názvů jazyka XAML je specializované obor názvů XML, stejně jako XAML je specializovaná forma XML a používá základní XML formulář pro jeho značek. V kódu, deklarace oboru názvů jazyka XAML a její mapování prostřednictvím `xmlns` atribut použitá pro element. `xmlns` Prohlášení stejného elementu, který oboru názvů jazyka XAML deklarovaného v souboru. Deklarace oboru názvů jazyka XAML provedené element je platná pro daný element, všechny atributy tohoto prvku a všechny podřízené objekty tohoto elementu. Atributy můžete použít obory názvů jazyka XAML, který není stejný jako elementu, který obsahuje atribut tak dlouho, dokud samotný název atributu odkazuje předponu jako součást názvu atributu v kódu.  
  
 Rozdíl v oboru názvů jazyka XAML a obor názvů XML je, že na obor názvů XML lze použít pro referenční schéma nebo může být sloužící k odlišení jednoduše entity. Pro jazyk XAML typy a členy jako použít v jazyce XAML musí být vyřešen nakonec k zálohování typy a koncepty schématu XML nelze použít i k této možnosti. Oboru názvů jazyka XAML obsahuje informace, že kontext schématu XAML musí mít k dispozici, aby bylo možné provést toto mapování typu.  
  
## <a name="xaml-namespace-components"></a>Součásti Namespace XAML  
 Definice oboru názvů jazyka XAML má dvě součásti: předpony a identifikátor. Každou z těchto součástí jsou k dispozici, pokud oboru názvů jazyka XAML je deklarován v kódu nebo definované v systému typu XAML.  
  
 Předpona, která může být libovolný řetězec, to povoluje [W3C obory názvů v XML 1.0 – specifikace](http://go.microsoft.com/fwlink/?LinkID=161735) . Podle konvence předpony jsou obvykle velmi krátké řetězce, protože předpona, která se opakuje tolikrát, kolikrát v souboru typické značek. Některé obory názvů jazyka XAML, které jsou určené pro použití v několika implementace XAML používat konkrétní konvenční předpony. Například je oboru názvů jazyka XAML jazyka XAML obvykle mapovat pomocí předponu `x`. Můžete definovat výchozí oboru názvů jazyka XAML, kde není zadané v definici předponu, ale je reprezentována jako prázdný řetězec, pokud definované nebo dotaz by.NET Framework XAML Services API. Obvykle je úmyslně zvolen výchozí obor názvů jazyka XAML za účelem podpory maximalizovaném okně množství vynechání předponu značky svým XAML implementace technologie a scénáře a vocabularies.  
  
 Identifikátor může být libovolný řetězec, to povoluje [W3C obory názvů v XML 1.0 – specifikace](http://go.microsoft.com/fwlink/?LinkID=161735). Podle konvence identifikátory pro obory názvů XML nebo obory názvů jazyka XAML často mají ve formě identifikátoru URI obvykle jako protokol kvalifikovaná absolutní identifikátor URI. Informace o verzi, definující konkrétní termínů XAML je často implicitní jako součást řetězec cesty. Obory názvů jazyka XAML přidat další identifikátor konvence nad rámec konvence XML URI. Pro obory názvů jazyka XAML komunikuje identifikátor informace, které je potřeba kontext schématu XAML za účelem vyřešení typy, které jsou definované jako elementy v tomto oboru názvů jazyka XAML, nebo pokud chcete vyřešit atributy pro členy.  
  
 Pro účely komunikaci informace na kontext schématu XAML identifikátor pro oboru názvů jazyka XAML stále může být ve formátu URI. Ale v takovém případě identifikátor URI je také deklarována jako odpovídající identifikátor v konkrétní sestavení nebo seznam sestavení. K tomu je potřeba v sestaveních zapisujících sestavení s <xref:System.Windows.Markup.XmlnsDefinitionAttribute>. Výchozí kontext schématu XAML v rozhraní .NET Framework XAML Services podporuje tato metoda identifikovat oboru názvů jazyka XAML a podpora chování na základě CLR typu řešení v prostředí s atributy sestavení. Obecně platí touto konvencí slouží pro případy, kdy kontext schématu XAML zahrnuje modulu CLR nebo je založen na výchozí kontext schématu XAML, který je potřebný pro čtení atributy CLR ze sestavení CLR.  
  
 Obory názvů jazyka XAML lze také identifikovat podle názvů, který komunikuje CLR obor názvů a definování typu sestavení. Touto konvencí se používá v případech, kde ne <xref:System.Windows.Markup.XmlnsDefinitionAttribute> uvedení existuje v sestavení, které obsahují typy. Touto konvencí je potenciálně složitější než konvenci URI a také je potenciálně nejednoznačnosti a duplikování, protože nejsou k dispozici více způsobů odkazy na sestavení.  
  
 Nejzákladnější formě identifikátor, který používá konvenci obor názvů a sestavení CLR vypadá takto:  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyShortName*  
  
 `clr-namespace:`a `; assembly=` jsou literálu součástí syntaxe.  
  
 *clrnsName* název řetězec, který identifikuje obor názvů CLR. Tento název řetězec obsahuje znaky interní tečku (.), které poskytují nápovědu, jak CLR obor názvů a jejich vztahu k jiných oborech názvů CLR.  
  
 *assemblyShortName* je název řetězce objektu sestavení, které definuje typy, které jsou užitečné v jazyce XAML. Typy, které mají být přistupovat prostřednictvím deklarované oboru názvů jazyka XAML se očekává, které sestavení a konkrétně deklarovat v rámci oboru názvů CLR určeného *clrnsName*. Tento název řetězce obvykle paralelní informace s vykazované <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType>.  
  
 Obsáhlejší definice konvence obor názvů a sestavení CLR vypadá takto:  
  
 `clr-namespace:`*clrnsName* `; assembly=` *assemblyName*  
  
 *assemblyName* představuje libovolný řetězec, který je právní jako <xref:System.Reflection.Assembly.Load%28System.String%29?displayProperty=nameWithType> vstupní. Tento řetězec může zahrnovat jazykovou verzi, veřejný klíč nebo informace o verzi (definice tyto koncepty jsou definovány v referenčním tématu pro <xref:System.Reflection.Assembly>). COFF formátu a důkaz (jako používá další přetížení <xref:System.Reflection.Assembly.Load%2A>) se nevztahují na sestavení XAML načítání účely; musí být všechny načíst informace o uvedené jako řetězec.  
  
 Určení veřejný klíč pro sestavení je užitečné pro XAML – zabezpečení, nebo pro odebrání možné nejednoznačnosti, který může existovat, pokud jsou načteny jednoduchý název sestavení, nebo předem existovat v doméně mezipaměti nebo aplikace. Další informace najdete v tématu [aspekty zabezpečení XAML](../../../docs/framework/xaml-services/xaml-security-considerations.md).  
  
## <a name="xaml-namespace-declarations-in-the-xaml-services-api"></a>Deklarace Namespace XAML v XAML Services rozhraní API  
 V rozhraní API služby XAML, je reprezentována deklaraci oboru názvů jazyka XAML <xref:System.Xaml.NamespaceDeclaration> objektu. Pokud jsou deklarace oboru názvů jazyka XAML v kódu, zavoláte <xref:System.Xaml.NamespaceDeclaration.%23ctor%28System.String%2CSystem.String%29> konstruktor. `ns` a `prefix` jako řetězce jsou zadány parametry a vstup zajistit pro tyto parametry odpovídá definici identifikátor oboru názvů jazyka XAML a předponu oboru názvů jazyka XAML podle dříve v tomto tématu.  
  
 Pokud jsou zkoumání informace oboru názvů jazyka XAML jako součást datový proud uzlu XAML nebo prostřednictvím jiný přístup k systému typ XAML <xref:System.Xaml.NamespaceDeclaration.Namespace%2A?displayProperty=nameWithType> sestavy identifikátor oboru názvů jazyka XAML a <xref:System.Xaml.NamespaceDeclaration.Prefix%2A?displayProperty=nameWithType> sestavy Předpona oboru názvů jazyka XAML.  
  
 V datový proud uzlu XAML může se objevit informace oboru názvů jazyka XAML jako uzlu XAML, který předchází entity, na který se vztahuje. To zahrnuje případech, kde informace oboru názvů jazyka XAML předchází `StartObject` kořenového prvku XAML. Další informace najdete v tématu [struktury datový proud uzlu XAML principy a koncepty](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md).  
  
 Pro mnoho scénářů, které používají rozhraní .NET Framework XAML Services API očekává se existovat alespoň jednu deklaraci oboru názvů jazyka XAML a deklaraci musí obsahovat nebo odkazovat na informace, které je požadované pro kontext schématu XAML. Obory názvů jazyka XAML musí zadat sestavení, které může být načten nebo překládání konkrétní typy v oborech názvů a sestavení, které jsou již načten nebo znáte kontext schématu XAML.  
  
 Chcete-li vygenerovat datový proud uzlu XAML, musí být k dispozici prostřednictvím kontext schématu XAML informací o typu XAML. Informace o typu XAML nelze určit bez první zjišťování relevantní oboru názvů jazyka XAML pro každý uzel k vytvoření. V tomto okamžiku ještě jsou vytvořeny žádné instance typy, ale kontext schématu XAML může potřebovat vyhledat informace z definice sestavení a typ zálohování. Třeba, aby bylo možné zpracovat kód `<Party><PartyFavor/></Party>`, kontext schématu XAML musí být schopní určit název a typ `ContentProperty` z `Party`a proto taky musíte znát informace oboru názvů jazyka XAML pro `Party` a `PartyFavor`. V případě výchozí kontext schématu XAML sestavy statickou reflexe většinu informací o systému XAML typu, který je potřebný pro generování v datový proud uzlu XAML typ uzly.  
  
 Chcete-li vygenerovat grafu objektu z datový proud uzlu XAML, musí existovat deklarace oboru názvů jazyka XAML pro každý XAML předponu používá v původní kód a zaznamenaná v datový proud uzlu XAML. V tomto okamžiku vytváření instancí a dojde k true mapování typu chování.  
  
 Pokud potřebujete předem zadat informace o oboru názvů jazyka XAML, v případech, kde není definován oboru názvů jazyka XAML kontext schématu XAML, který má používat, který chcete do kódu jednou technik, můžete je deklarovat deklarace oboru názvů XML v <xref:System.Xml.XmlParserContext> pro <xref:System.Xml.XmlReader>. Pak použijte <xref:System.Xml.XmlReader> jako vstup pro konstruktor čtečky XAML, nebo <xref:System.Xaml.XamlServices.Load%28System.Xml.XmlReader%29?displayProperty=nameWithType>.  
  
 Jsou dva další rozhraní API, které jsou relevantní pro zpracování v rozhraní .NET Framework XAML Services oboru názvů jazyka XAML atributy <xref:System.Windows.Markup.XmlnsDefinitionAttribute> a <xref:System.Windows.Markup.XmlnsPrefixAttribute>. Tyto atributy se používají k sestavení. <xref:System.Windows.Markup.XmlnsDefinitionAttribute>je používán kontext schématu XAML interpretovat všechny deklaraci oboru názvů jazyka XAML, která obsahuje identifikátor URI. <xref:System.Windows.Markup.XmlnsPrefixAttribute>používá nástroje, které emitování XAML tak, aby konkrétní oboru názvů jazyka XAML lze serializovat předvídatelný předponu. Další informace najdete v tématu [XAML-Related CLR atributy pro vlastní typy a knihovny](../../../docs/framework/xaml-services/xaml-related-clr-attributes-for-custom-types-and-libraries.md).  
  
## <a name="see-also"></a>Viz také  
 [Principy struktur datový proud uzlu XAML a koncepty](../../../docs/framework/xaml-services/understanding-xaml-node-stream-structures-and-concepts.md)
