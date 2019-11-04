---
title: Vlastnosti závislosti jen pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: a849b835bab832a4ddb8d594d1788ab062f4284e
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459002"
---
# <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení
Toto téma popisuje vlastnosti závislosti jen pro čtení, včetně existujících vlastností závislosti jen pro čtení a scénářů a technik pro vytvoření vlastní vlastnosti závislosti jen pro čtení.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 V tomto tématu se předpokládá, že rozumíte základním scénářům implementace vlastnosti závislosti a způsobu, jakým se aplikují metadata na vlastní vlastnost závislosti. Podívejte se na téma [vlastnosti vlastní závislosti](custom-dependency-properties.md) a [metadata vlastnosti závislosti](dependency-property-metadata.md) pro kontext.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Existující vlastnosti závislosti jen pro čtení  
 Některé vlastnosti závislosti definované v rozhraní [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] Framework jsou jen pro čtení. Typickým důvodem pro zadání vlastnosti závislosti jen pro čtení je, že se jedná o vlastnosti, které by měly být použity pro určení stavu, ale pokud je tento stav ovlivněn mnoha faktory, ale pouze nastavení vlastnosti na tento stav není žádoucí z Perspektiva návrhu uživatelského rozhraní Například vlastnost <xref:System.Windows.UIElement.IsMouseOver%2A> je ve skutečnosti jenom zpřístupnění stav, jak je určeno z vstupu myši. Jakýkoli pokus o nastavení této hodnoty programově obcházením skutečného vstupu myši by bylo nepředvídatelné a způsobil nekonzistenci.  
  
 Vzhledem k tomu, že není možné napravovat vlastnosti závislosti jen pro čtení, nejsou vhodné pro mnoho scénářů, pro které vlastnosti závislosti běžně nabízejí řešení (konkrétně: datové vazby, přímo ovládacích k hodnotě, ověřování, animaci a dědičnosti). Bez ohledu na to, vlastnosti závislosti jen pro čtení mají stále k dispozici některé další funkce podporované vlastnostmi závislosti v systému vlastností. Nejdůležitější zbývající možností je, že vlastnost závislosti, která je jen pro čtení, může být stále používána jako Trigger vlastnosti ve stylu. Aktivační události nemůžete povolit s normální vlastností modulu CLR (Common Language Runtime). musí se jednat o vlastnost závislosti. Výše uvedená vlastnost <xref:System.Windows.UIElement.IsMouseOver%2A> představuje dokonalý příklad scénáře, kde může být poměrně užitečná pro definování stylu ovládacího prvku, kde některá viditelná vlastnost, jako je například pozadí, popředí nebo podobné vlastnosti složených prvků v rámci ovládacího prvku, budou změní se, když uživatel umístí ukazatel myši nad určitou definovanou oblast vašeho ovládacího prvku. Změny vlastnosti závislosti jen pro čtení mohou být zjištěny a hlášeny základními procesy neplatných v systému vlastností a to ve skutečnosti podporuje funkci triggeru vlastností interně.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Vytváření vlastních vlastností závislosti jen pro čtení  
 Nezapomeňte si přečtěte část výše v tématu Proč vlastnosti závislosti jen pro čtení nebudou fungovat pro řadu typických scénářů pro vlastnosti závislostí. Pokud ale máte vhodný scénář, možná budete chtít vytvořit vlastní vlastnost závislosti jen pro čtení.  
  
 Většina procesu vytvoření vlastnosti závislosti jen pro čtení je stejná jako v případě, že je popsána v tématech [vlastní vlastnosti závislosti](custom-dependency-properties.md) a [implementace vlastností závislosti](how-to-implement-a-dependency-property.md) . Existují tři důležité rozdíly:  
  
- Při registraci vlastnosti zavolejte metodu <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> namísto normální <xref:System.Windows.DependencyProperty.Register%2A> metody pro registraci vlastností.  
  
- Při implementaci vlastnosti "Obálka" CLR se ujistěte, že obálka není nastavena jako implementace, takže neexistuje žádná nekonzistence ve stavu jen pro čtení pro veřejnou obálku, kterou vystavíte.  
  
- Objekt vrácený registrací jen pro čtení je <xref:System.Windows.DependencyPropertyKey> místo <xref:System.Windows.DependencyProperty>. Toto pole byste měli i nadále ukládat jako člen, ale obvykle byste mu nechtěli být veřejným členem tohoto typu.  
  
 Jakékoli soukromé pole nebo hodnota, které jste zálohovali ze své vlastnosti závislosti jen pro čtení, je možné samozřejmě plně zapisovat pomocí libovolné logiky, kterou určíte. Nejjednodušším způsobem, jak vlastnost nastavit buď zpočátku, nebo jako součást logiky prostředí runtime, je však použít rozhraní API systému vlastností namísto obcházení systému vlastností a přímé nastavení soukromého pole pro zálohování. Konkrétně je k dispozici podpis <xref:System.Windows.DependencyObject.SetValue%2A>, který přijímá parametr typu <xref:System.Windows.DependencyPropertyKey>. Jak a kde nastavíte tuto hodnotu programově v rámci logiky vaší aplikace, bude mít vliv na to, jak můžete chtít nastavit přístup k <xref:System.Windows.DependencyPropertyKey> vytvořenému při první registraci vlastnosti závislosti. Pokud tuto logiku zpracujete vše v rámci třídy, můžete ji nastavit jako soukromou, nebo pokud požadujete, aby byla nastavena z jiných částí sestavení, které můžete nastavit jako interní. Jedním z přístupů je volat <xref:System.Windows.DependencyObject.SetValue%2A> v rámci obslužné rutiny události třídy příslušné události, která informuje o instanci třídy, že je nutné změnit hodnotu uložené vlastnosti. Dalším přístupem je propojení vlastností závislosti společně s použitím spárovaných <xref:System.Windows.PropertyChangedCallback> a <xref:System.Windows.CoerceValueCallback> zpětná volání jako součást metadat těchto vlastností během registrace.  
  
 Vzhledem k tomu, že <xref:System.Windows.DependencyPropertyKey> je privátní a nešíří se systémem vlastností mimo váš kód, má vlastnost závislosti jen pro čtení lepší nastavení zabezpečení než vlastnost závislosti pro čtení a zápis. U vlastnosti závislosti pro čtení i zápis je identifikační pole explicitně nebo implicitně veřejné, a proto je tato vlastnost široce nastavitelná. Další podrobnosti najdete v tématu [zabezpečení vlastností závislostí](dependency-property-security.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
