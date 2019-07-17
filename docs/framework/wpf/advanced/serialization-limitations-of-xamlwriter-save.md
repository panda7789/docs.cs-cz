---
title: Omezení serializace XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: f743f3de505904854be8aab59e9d3ad14ee64581
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68238623"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Omezení serializace XamlWriter.Save
Rozhraní API <xref:System.Windows.Markup.XamlWriter.Save%2A> slouží k serializaci obsahu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace jako [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru. Existují však některé důležité omezení v co přesně je serializována. Tato omezení a některé obecné aspekty jsou popsány v tomto tématu.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Za běhu, ne návrhu zastupování  
 Základní princip co serializován voláním <xref:System.Windows.Markup.XamlWriter.Save%2A> je, že výsledkem bude reprezentaci objektu serializována v době běhu. Mnoho vlastností návrhu původní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] soubor již může optimalizované nebo ztráty v čase, který [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je načteno jako objektů v paměti a nejsou zachovány při volání <xref:System.Windows.Markup.XamlWriter.Save%2A> k serializaci. Serializovaná výsledek je efektivní reprezentace konstruovaný logické stromové struktuře aplikace, ale ne nutně původní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , který jej vytvořil. Tyto problémy být velmi obtížné použít <xref:System.Windows.Markup.XamlWriter.Save%2A> serializace jako součást rozsáhlý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] návrhovou plochu.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Serializace je samostatná  
 Serializovaná výstupu <xref:System.Windows.Markup.XamlWriter.Save%2A> je samostatný; všechno, co se serializuje je obsaženo uvnitř [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jednu stránku, jeden kořenový element a žádné externí odkazy na jiné než [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]. Například pokud vaše stránka odkazované prostředky ze zdrojů aplikace, tyto se zobrazí jako by byly součástí na stránce serializována.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Reference na rozšíření se přistoupit přes ukazatel  
 Běžné odkazy na objekty provedené různých formátech rozšíření značek, jako například `StaticResource` nebo `Binding`, bude lze přistoupit přes ukazatel pomocí procesu serializace. Byly již dereferencována v době spuštění aplikace byly vytvořeny objektů v paměti a <xref:System.Windows.Markup.XamlWriter.Save%2A> logiku opakování není původní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a obnovit tyto odkazy do serializovaná výstupu. Zablokuje potenciálně všechny datové vazby nebo prostředků získané hodnota, která má být hodnota posledního používá reprezentaci za běhu s pouze omezené nebo nepřímé schopnost rozlišovat taková hodnota z libovolné jiné hodnoty nastavit místně. Bitové kopie jsou také serializovat jako objekt odkazy na Image, protože existují v projektu, nikoli jako původní odkazy na zdroje, ztráta libovolné název souboru nebo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] původně bylo odkazováno. Dokonce i prostředky, které jsou deklarované na stejné stránce se zobrazují serializovaná do bodu, kde jsou bylo odkazováno, místo zachován jako klíč na kolekci prostředků.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Zpracování událostí je Nezachované  
 Když obslužným rutinám, které jsou přidány prostřednictvím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jsou serializován, že nejsou zachovány. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bez použití modelu code-behind (a také bez mechanismu související x: Code) nemá možnost nijak procesní logiky modulu runtime serializace. Protože serializace je samostatná a omezené na Logická stromová struktura, neexistuje žádné zařízení pro ukládání obslužné rutiny událostí. V důsledku toho atributech obslužné rutiny událostí, samotného atributu a řetězcovou hodnotu, která pojmenuje obslužnou rutinu, odeberou se z výstupu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Reálné scénáře použití pro funkci XAMLWriter.Save  
 Zatímco omezení uvedená tady jsou poměrně podstatné, jsou stále několik odpovídající scénáře použití <xref:System.Windows.Markup.XamlWriter.Save%2A> pro serializaci.  
  
- Vektor nebo grafického výstupu: Výstup vykresleného oblasti je možné reprodukovat stejné vektoru nebo grafické při znovu načten.  
  
- Formátovaný text a flow dokumenty: Text a všechny element formátování a element členství ve skupině v ní je zachována ve výstupu. To může být užitečné pro mechanismy, které přibližný funkce schránky.  
  
- Zachování dat obchodních objektů: Pokud jste uložili data ve vlastních elementů, jako například [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat, pokud vaše obchodní objekty podle základní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] tyto objekty obchodní pravidla, například vlastní konstruktory a převodu pro hodnoty vlastnosti podle odkazu, může být perpetuated prostřednictvím serializace.
