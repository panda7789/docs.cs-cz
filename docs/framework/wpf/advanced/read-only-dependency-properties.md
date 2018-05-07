---
title: Vlastnosti závislosti jen pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 2850dd86ffbe2c6698821218dee5d870fc58e89b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení
Toto téma popisuje vlastnosti jen pro čtení závislostí, včetně existující vlastností závislostí jen pro čtení a scénáře a metody pro vytváření vlastnost vlastní závislosti jen pro čtení.  
  

  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že chápete základní scénáře implementace vlastnost závislosti a jak je použito metadata pro vlastnost vlastní závislosti. V tématu [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) a [metadat vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-property-metadata.md) pro kontext.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Existující vlastností závislostí jen pro čtení  
 Některé vlastnosti závislosti definovaný v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] framework jsou jen pro čtení. Typický případ pro zadání vlastnost závislosti jen pro čtení je, že jsou vlastnosti, které se mají použít pro zjištění stavu, ale kde vliv různé faktory, ale jenom nastavení vlastnosti na tento stav není žádoucí z tohoto stavu uživatelské rozhraní návrhu perspektivy. Například vlastnost <xref:System.Windows.UIElement.IsMouseOver%2A> je skutečně právě zpřístupnění stavu určené vstup myši. Pokusy o tuto hodnotu nastavit prostřednictvím kódu programu obcházení vstup true myši by nepředvídatelné a způsobí nekonzistenci.  
  
 Na základě nebude nastavit, nejsou vhodné pro mnoho scénářů, pro které závislost vlastnosti obvykle nabízejí řešení vlastností závislostí jen pro čtení (konkrétně: datové vazby, přímo stylable hodnotu, ověření, animace a dědičnost). Navzdory nebude závislostí nastavit, jen pro čtení vlastnosti ještě některé další možnosti nepodporuje vlastností závislostí v systému vlastnost. Nejdůležitější funkce zbývající je, že vlastnost jen pro čtení závislosti pořád můžou použít jako trigger vlastností ve stylu. Nelze povolit aktivační události normální [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost; musí se jednat o vlastnosti závislosti. Výše uvedené <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost je ideální příklad scénáře, kde může být velmi užitečné k definování stylu pro ovládací prvek, kde některé vlastnost visible například na pozadí, popředí nebo podobné vlastnosti kompletní složený elementů v rámci ovládací prvek se změní při umístění myši nad některé definované oblast ovládacího prvku. Změny ve vlastnosti jen pro čtení závislostí také můžete zjistil a hlášené vlastnost systému vyplývajících zneplatnění procesy a to ve skutečnosti podporuje vlastnost aktivační události funkce interně.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Vytváření vlastní závislosti jen pro čtení vlastnosti  
 Nezapomeňte si přečíst v části výše týkající se proč vlastnosti jen pro čtení závislosti nefungují pro mnoho scénářů typické vlastnost závislosti. Ale pokud máte příslušné scénáři, můžete vytvořit vlastní vlastnost závislosti jen pro čtení.  
  
 Velká část procesu vytváření vlastnost závislosti jen pro čtení je stejné, jako je popsaná v [vlastní závislosti vlastnosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md) a [implementovat vlastnost závislosti](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) témata. Existují tři důležité rozdíly:  
  
-   Při registraci vaší vlastností, zavolejte <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> metody místo normální <xref:System.Windows.DependencyProperty.Register%2A> metoda pro registraci vlastnost.  
  
-   Při implementaci [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] "obálky" vlastnost měli jistotu, obálku příliš nemá sadu implementace, tak, aby bylo žádné nekonzistence ve stavu jen pro čtení pro veřejné obálku vystavit.  
  
-   Objekt vrácený registrace jen pro čtení je <xref:System.Windows.DependencyPropertyKey> místo <xref:System.Windows.DependencyProperty>. Měli byste stále uložit toto pole jako člena, ale obvykle vám nebude nastavte jej jako veřejné člena typu.  
  
 Ať soukromé pole nebo hodnotu, kterou jste zálohování vaší vlastnosti jen pro čtení závislosti samozřejmě může být plně zapisovatelné pomocí libovolnou logiku rozhodnete. Nejjednodušší způsob, jak nastavit vlastnost původně nebo jako součást logiky runtime je však používat vlastnost systému [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], namísto obcházení vlastnost systému a nastavení privátní základní pole přímo. Konkrétně je podpis <xref:System.Windows.DependencyObject.SetValue%2A> který přijme parametr typu <xref:System.Windows.DependencyPropertyKey>. Jak a kde se tato hodnota nastavit prostřednictvím kódu programu v rámci logiky aplikace bude mít vliv na způsob nastavení přístupu na <xref:System.Windows.DependencyPropertyKey> vytvořen při první registraci vlastnost závislosti. Pokud zpracovat tuto logiku všechny v rámci třídy vám může způsobit, že privátní, nebo pokud budete požadovat, aby nastavit z dalších částí sestavení může ji nastavit vnitřní. Jeden z přístupů je volat <xref:System.Windows.DependencyObject.SetValue%2A> v rámci třídy obslužné rutiny události relevantní události, které informují instance třídy, které je potřeba změnit hodnotu vlastnosti uložené. Další možností je ke svázání vlastností závislostí společně s použitím spárovat <xref:System.Windows.PropertyChangedCallback> a <xref:System.Windows.CoerceValueCallback> zpětná volání v rámci tyto vlastnosti metadat během registrace.  
  
 Protože <xref:System.Windows.DependencyPropertyKey> soukromá a není rozšíří vlastnost systému mimo váš kód, vlastnost závislosti jen pro čtení má lepší nastavení zabezpečení než vlastnost závislosti pro čtení a zápis. Pro vlastnost závislosti pro čtení a zápis je pole identifikační explicitně nebo implicitně veřejné a proto je široce nastavit vlastnost. Další podrobnosti najdete v části [zabezpečení vlastnost závislosti](../../../../docs/framework/wpf/advanced/dependency-property-security.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
