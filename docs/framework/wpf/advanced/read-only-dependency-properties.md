---
title: Vlastnosti závislosti jen pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 8adc90182f0f42f52e6ace4e13c68acb3539516b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187184"
---
# <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení
Toto téma popisuje vlastnosti závislostí jen pro čtení, včetně existujících vlastností závislostí jen pro čtení a scénářů a technik pro vytvoření vlastní vlastnosti závislosti jen pro čtení.  

<a name="prerequisites"></a>
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že rozumíte základním scénářům implementace vlastnosti závislosti a způsobu použití metadat na vlastní vlastnost závislosti. Viz [Vlastní vlastnosti závislostí](custom-dependency-properties.md) a [metadata vlastností závislostí](dependency-property-metadata.md) pro kontext.  
  
<a name="existing"></a>
## <a name="existing-read-only-dependency-properties"></a>Existující vlastnosti závislostí jen pro čtení  
 Některé vlastnosti závislostí definované [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] v rámci jsou jen pro čtení. Typickým důvodem pro určení vlastnosti závislosti jen pro čtení je, že se jedná o vlastnosti, které by měly být použity pro určení stavu, ale kde je tento stav ovlivněn velkým množstvím faktorů, ale pouze nastavení vlastnosti do tohoto stavu není žádoucí z perspektivu návrhu uživatelského rozhraní. Například vlastnost <xref:System.Windows.UIElement.IsMouseOver%2A> je opravdu jen navařování stavu, jak je určeno ze vstupu myši. Jakýkoli pokus o nastavení této hodnoty programově obcházením vstupu myši true by byl nepředvídatelný a způsobil by nekonzistenci.  
  
 Vzhledem k tomu, že není nastavitelná, vlastnosti závislostí jen pro čtení nejsou vhodné pro mnoho scénářů, pro které vlastnosti závislostí obvykle nabízejí řešení (konkrétně: datová vazba, přímo přizpůsobitelné hodnotě, ověření, animace, dědičnost). Přesto, že není nastavena, vlastnosti závislostí jen pro čtení stále mají některé další možnosti podporované vlastnostmi závislostí v systému vlastností. Nejdůležitější zbývající možnost je, že závislost jen pro čtení vlastnost může být stále použit jako aktivační událost vlastnosti ve stylu. Nelze povolit aktivační události s normální common jazyk runtime (CLR) vlastnost; musí být vlastnost závislosti. Výše uvedená <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost je dokonalým příkladem scénáře, kde může být velmi užitečné definovat styl pro ovládací prvek, kde některé viditelné vlastnosti, jako je například pozadí, popředí nebo podobné vlastnosti složených prvků v rámci ovládacího prvku se změní, když uživatel umístí myší nad některé definované oblasti ovládacího prvku. Změny ve vlastnosti závislosti jen pro čtení mohou být také zjištěny a hlášeny vlastními procesy neplatnosti systému vlastností, což ve skutečnosti interně podporuje funkci aktivační události vlastnosti.  
  
<a name="new"></a>
## <a name="creating-custom-read-only-dependency-properties"></a>Vytváření vlastních vlastností závislostí jen pro čtení  
 Ujistěte se, že si přečtěte výše uvedený oddíl o tom, proč vlastnosti závislostí jen pro čtení nebude fungovat pro mnoho typické scénáře závislostí vlastností. Ale pokud máte vhodný scénář, můžete vytvořit vlastní vlastnost závislostí jen pro čtení.  
  
 Většina procesu vytváření vlastnosti závislosti jen pro čtení je stejná, jak je popsáno v [tématech Vlastnosti vlastní závislosta](custom-dependency-properties.md) a [implementovat vlastnosti závislostí.](how-to-implement-a-dependency-property.md) Existují tři důležité rozdíly:  
  
- Při registraci vaší vlastnosti volejte metodu namísto <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> normální <xref:System.Windows.DependencyProperty.Register%2A> metody pro registraci vlastnosti.  
  
- Při implementaci CLR "obálka" vlastnost, ujistěte se, že obálka také nemá sadu implementace, tak, aby neexistuje žádná nekonzistence ve stavu jen pro čtení pro veřejné obálky vystavit.  
  
- Objekt vrácený jen pro čtení <xref:System.Windows.DependencyPropertyKey> registrace <xref:System.Windows.DependencyProperty>je spíše než . Toto pole byste měli stále ukládat jako člen, ale obvykle byste z něj neučinili veřejného člena typu.  
  
 Bez ohledu na soukromé pole nebo hodnotu, kterou máte podporu vlastnosti závislosti jen pro čtení, může být samozřejmě plně zapisovatelná pomocí jakékoli logiky, kterou se rozhodnete. Nejjednodušší způsob, jak nastavit vlastnost buď zpočátku nebo jako součást logiky runtime je použití vlastnosti systému API, spíše než obcházení systému vlastností a nastavení soukromého pole zálohování přímo. Zejména je <xref:System.Windows.DependencyObject.SetValue%2A> podpis, který přijímá parametr typu <xref:System.Windows.DependencyPropertyKey>. Jak a kde nastavit tuto hodnotu programově v rámci aplikační logiky <xref:System.Windows.DependencyPropertyKey> bude mít vliv na způsob, jakým můžete chtít nastavit přístup k vytvořené při první registraci vlastnost ionty. Pokud zpracováváte tuto logiku všechny v rámci třídy můžete provést soukromé, nebo pokud požadujete, aby byla nastavena z jiných částí sestavení můžete nastavit interní. Jedním z přístupů je volání <xref:System.Windows.DependencyObject.SetValue%2A> v rámci obslužné rutiny události třídy relevantní události, která informuje instanci třídy, že je třeba změnit hodnotu uložené vlastnosti. Dalším přístupem je spojit vlastnosti závislostí pomocí spárovaných <xref:System.Windows.PropertyChangedCallback> a <xref:System.Windows.CoerceValueCallback> zpětná volání jako součást metadat těchto vlastností během registrace.  
  
 Vzhledem <xref:System.Windows.DependencyPropertyKey> k tomu, že je privátní a není šířensystémem vlastností mimo váš kód, vlastnost závislosti jen pro čtení má lepší nastavení zabezpečení než vlastnost závislost í čtení a zápisu. Pro vlastnost závislost čtení a zápisu je identifikační pole explicitně nebo implicitně veřejné a proto je vlastnost široce nastavitelná. Další podrobnosti naleznete v [tématu Zabezpečení vlastností závislostí](dependency-property-security.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
