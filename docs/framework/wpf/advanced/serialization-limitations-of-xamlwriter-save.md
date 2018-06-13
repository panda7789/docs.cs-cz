---
title: Omezení serializace XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: cbe8d517b8794f6aae7190457a077422d235acb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33547960"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Omezení serializace XamlWriter.Save
[!INCLUDE[TLA#tla_api](../../../../includes/tlasharptla-api-md.md)] <xref:System.Windows.Markup.XamlWriter.Save%2A> Lze použít k serializaci obsah [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace jako [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru. Nicméně existují určitá omezení upozorňují na důležité v přesně to, co je serializováno. Tato omezení a některé obecné aspekty jsou popsány v tomto tématu.  
  
 
  
<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Run-Time, není návrhu reprezentace  
 Základní filosofie z serializovat volání <xref:System.Windows.Markup.XamlWriter.Save%2A> je, že výsledkem bude reprezentace objektu serializována v době spuštění. Mnoho vlastnosti doby návrhu původního [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru již lze optimalizované nebo ztratit na době, který [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je načteno jako objekty v paměti a nejsou zachována při volání <xref:System.Windows.Markup.XamlWriter.Save%2A> k serializaci. Serializovaná výsledkem je účinné reprezentace sestavené logickém stromu. aplikace, ale nemusí nutně prokázat původního [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] který ho vytvořil. Tyto problémy být velmi obtížné použít <xref:System.Windows.Markup.XamlWriter.Save%2A> serializace jako součást rozsáhlý [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] návrhovou plochu.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Serializace je úplný a samostatný  
 Serializovaná výstup <xref:System.Windows.Markup.XamlWriter.Save%2A> je samostatný; vše, co je serializováno se nachází v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jediné stránce s jeden kořenový element a žádné externí odkazy, jinak než [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)]. Například pokud stránku odkazováno prostředky z prostředků aplikace, tyto se zobrazí jako by byly součástí stránce serializována.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Reference na rozšíření jsou vyhodnoceny odkazy  
 Běžné odkazy na objekty provedené různými formáty rozšíření značek, například `StaticResource` nebo `Binding`, budou vyhodnoceny odkazy procesem serializace. Tyto byly již vyhodnoceny odkazy v době, modulem runtime aplikace byly vytvořeny objekty v paměti a <xref:System.Windows.Markup.XamlWriter.Save%2A> logiku není pokroku původní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] a obnovit tyto odkazy na serializovaných výstup. To se zablokuje potenciálně žádné Vycentrovat nebo prostředek získat hodnota, která má být hodnota poslední používané reprezentace spuštění, se jenom omezené nebo nepřímý schopností k rozlišení tuto hodnotu z jakoukoli jinou hodnotu nastavit místně. Bitové kopie jsou také serializován jako objekt odkazů na obrázky, které jsou v projektu, nikoli jako původní odkazů na zdroje, ať filename ztráty nebo [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] původně bylo odkazováno. I prostředky, které jsou deklarované v rámci stejné stránce se zobrazují serializovaných do bodu, kde budou odkazují, místo se zachovají jako klíč kolekci prostředků.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Zpracování událostí je, není zachována.  
 Když obslužné rutiny událostí, které jsou přidány prostřednictvím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] se serializuje, že nejsou zachována. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bez kódu (a také bez mechanismus související x: Code) nemá žádnou možnost serializace Procedurální logika modulu runtime. Protože serializace je úplný a samostatný a je omezený na logickém stromu, neexistuje žádné zařízení pro ukládání obslužné rutiny událostí. V důsledku toho atributy obslužná rutina události, atribut sám a řetězcovou hodnotu, kterou názvy obslužná rutina, se odeberou z výstupu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Realistické scénáře pro použití XAMLWriter.Save  
 Při omezení uvedených zde jsou poměrně dlouhou, stále existuje několik situací vhodné pro použití <xref:System.Windows.Markup.XamlWriter.Save%2A> pro serializaci.  
  
-   Vector nebo grafické výstup: výstup vykreslené oblasti je možné použít pro reprodukci stejné vektoru nebo grafiky při znovu načíst.  
  
-   Formátovaný text a toku dokumenty: Text a všechny element formátování a element členství ve skupině v něm je zachována ve výstupu. To může být užitečné pro mechanismy, které Přibližná funkce schránky.  
  
-   Zachování dat objektu obchodní: Pokud jste uložili data v vlastní prvky, jako například [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data, takže pokud obchodní objekty podle základní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pravidla například poskytnutí vlastní konstruktory a převod odkazem hodnoty vlastností, Tyto objekty firmy můžete perpetuated prostřednictvím serializace.
