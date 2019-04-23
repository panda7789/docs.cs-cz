---
title: Vlastnosti závislosti jen pro čtení
ms.date: 03/30/2017
helpviewer_keywords:
- dependency properties [WPF], read-only
- read-only dependency properties [WPF]
ms.assetid: f23d6ec9-3780-4c09-a2ff-b2f0a2deddf1
ms.openlocfilehash: 45385e3e3eb8e756008a0d9ef560e061f9a31964
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162420"
---
# <a name="read-only-dependency-properties"></a>Vlastnosti závislosti jen pro čtení
Toto téma popisuje vlastnosti závislosti jen pro čtení, včetně existující vlastnosti závislosti jen pro čtení a scénáře a postupy pro vytvoření vlastnosti vlastní závislosti jen pro čtení.  

<a name="prerequisites"></a>   
## <a name="prerequisites"></a>Požadavky  
 Toto téma předpokládá, že chápete základní scénáře implementace vlastnosti závislosti a jak je použito metadat pro vlastnost vlastní závislosti. Zobrazit [vlastní vlastnosti závislosti](custom-dependency-properties.md) a [Metadata vlastností závislosti](dependency-property-metadata.md) pro kontext.  
  
<a name="existing"></a>   
## <a name="existing-read-only-dependency-properties"></a>Existující vlastnosti závislosti jen pro čtení  
 Některé vlastnosti závislosti definované v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] framework jsou jen pro čtení. Typické důvod pro zadání vlastnosti závislosti jen pro čtení je, že jsou vlastnosti, která má být použita pro určení stavu, ale pokud státu je ovlivněno různé faktory, ale jenom nastavení není vlastnost, která má tento stav žádoucí Perspektiva návrhu uživatelského rozhraní. Například vlastnost <xref:System.Windows.UIElement.IsMouseOver%2A> je vlastně jenom zpřístupnění stavu počítáno vstup myši. Jakékoli pokusy o tuto hodnotu nastavit prostřednictvím kódu programu pomocí obcházení vstup myši true by nepředvídatelný a způsobí nekonzistenci.  
  
 Tím, že nebude nastavitelná při čekání, nejsou vhodné pro mnoho scénářů, pro které závislosti vlastnosti obvykle nabízejí řešení vlastnosti závislosti jen pro čtení (konkrétně: Datová vazba přímo s podporou stylů na hodnotu, ověření, animace, dědičnost). Bez ohledu na závislost nastavitelná při čekání, jen pro čtení mohou být vlastnosti ještě některé další možnosti nepodporuje vlastnosti závislosti v systému vlastností. Nejdůležitější zbývající možnosti je, že vlastnosti závislosti jen pro čtení může i nadále sloužit jako aktivační procedura vlastností ve stylu. Nelze povolit triggery normální [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost; musí se jednat o vlastnosti závislosti. Výše uvedenému <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost je ideální příklad scénáře, ve kterém může být velmi užitečný k definování stylu pro ovládací prvek, pokud některé vlastnosti visible například na pozadí, popředí nebo podobné vlastnosti složené prvky v rámci ovládací prvek se změní při umístění myši nad některé definované oblasti ovládacího prvku. Změny ve vlastnosti závislosti jen pro čtení můžete také být zjištěna a ohlášených vlastností systému vyplývajících zneplatnění procesy, a to ve skutečnosti podporuje funkci aktivační události vlastnost interně.  
  
<a name="new"></a>   
## <a name="creating-custom-read-only-dependency-properties"></a>Vytváří se vlastní závislosti jen pro čtení vlastnosti  
 Nezapomeňte si přečíst výše uvedené části týkající se proč vlastnosti závislosti jen pro čtení nebude fungovat pro řadu scénářů typické vlastnost závislosti. Ale pokud máte odpovídající scénáři, můžete chtít vytvořit vlastní vlastnosti závislosti jen pro čtení.  
  
 Velkou část procesu vytvoření vlastnosti závislosti jen pro čtení je stejný, jak je popsáno v [vlastní vlastnosti závislosti](custom-dependency-properties.md) a [implementace vlastnosti závislosti](how-to-implement-a-dependency-property.md) témata. Existují tři důležité rozdíly:  
  
-   Při registraci vaší vlastností, zavolejte <xref:System.Windows.DependencyProperty.RegisterReadOnly%2A> metoda místo normální <xref:System.Windows.DependencyProperty.Register%2A> metody pro registraci vlastnost.  
  
-   Při implementaci [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost "zabezpečenou obálku", ujistěte se, že obálku příliš nemá implementaci sady, tak, aby se žádné nekonzistence ve stavu jen pro čtení pro veřejné obálku zveřejníte.  
  
-   Objekt vrácený rutinou registrace jen pro čtení je <xref:System.Windows.DependencyPropertyKey> spíše než <xref:System.Windows.DependencyProperty>. Stále byste měli uložit toto pole jako člen, ale obvykle by usnadňují veřejného člena typu.  
  
 Jakýkoli soukromé pole nebo hodnotu, kterou jste zálohování vaší vlastnosti závislosti jen pro čtení samozřejmě může být plně zapisovat pomocí libovolné logiky rozhodnete. Nejjednodušší způsob, jak nastavit vlastnost původně nebo jako součást logiky modulu runtime je však používat systém vlastnost [!INCLUDE[TLA2#tla_api#plural](../../../../includes/tla2sharptla-apisharpplural-md.md)], namísto obcházení systému vlastností a nastavení privátní pomocné pole přímo. Zejména je podpis <xref:System.Windows.DependencyObject.SetValue%2A> , který přijímá parametr typu <xref:System.Windows.DependencyPropertyKey>. Jak a kde nastavíte hodnotu prostřednictvím kódu programu v rámci vaší aplikace logiky bude mít vliv na způsob nastavení přístupu na <xref:System.Windows.DependencyPropertyKey> vytvoří při první registraci vlastnost závislosti. Pokud zpracovat tuto logiku vše v rámci třídy vám může usnadnit privátní, nebo pokud chcete, aby nastavení z dalších částí sestavení, může ji nastavit interní. Jedním z přístupů je volat <xref:System.Windows.DependencyObject.SetValue%2A> v rámci třídy obslužná rutina události relevantní události, která informuje o tom, kterou je potřeba změnit hodnotu vlastnosti uloženou instanci třídy. Další možností je spojovat vlastnosti závislosti pomocí spárované <xref:System.Windows.PropertyChangedCallback> a <xref:System.Windows.CoerceValueCallback> zpětná volání jako součást těchto vlastností metadat během registrace.  
  
 Protože <xref:System.Windows.DependencyPropertyKey> je privátní a se nerozšíří vlastnost systému mimo váš kód, vlastnosti závislosti jen pro čtení má lepší než vlastnost závislosti pro čtení a zápis nastavení zabezpečení. Pro vlastnost závislosti pro čtení i zápis je explicitně nebo implicitně veřejné pole identifikační a proto je široce nastavitelnou vlastnost. Další podrobnosti najdete v části [zabezpečení vlastností závislosti](dependency-property-security.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Styly a šablony](../controls/styling-and-templating.md)
