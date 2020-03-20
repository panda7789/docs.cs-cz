---
title: Omezení serializace XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 96e917898320fb5d49f4e7dfc27daa7750af9d41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174365"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Omezení serializace XamlWriter.Save
Rozhraní <xref:System.Windows.Markup.XamlWriter.Save%2A> API lze serializovat obsah [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace jako [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor. Existují však některá významná omezení přesně v tom, co je serializováno. Tato omezení a některé obecné aspekty jsou popsány v tomto tématu.  

<a name="Run_Time__Not_Design_Time_Representation"></a>
## <a name="run-time-not-design-time-representation"></a>Znázornění za běhu, nikoli návrhu  
 Základní filozofie co je serializován volání <xref:System.Windows.Markup.XamlWriter.Save%2A> je, že výsledkem bude reprezentace objektu serializována, za běhu. Mnoho vlastností návrhu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] původního souboru již může být optimalizováno nebo ztraceno v době, kdy [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] je <xref:System.Windows.Markup.XamlWriter.Save%2A> načten jako objekty v paměti, a nejsou zachovány při volání serializace. Serializovaný výsledek je efektivní reprezentace vytvořeného logického stromu aplikace, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ale ne nutně originálu, který ji vytvořil. Tyto problémy ztěžují použití <xref:System.Windows.Markup.XamlWriter.Save%2A> serializace jako součást [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rozsáhlé návrhové plochy.  
  
<a name="Serialization_is_Self_Contained"></a>
## <a name="serialization-is-self-contained"></a>Serializace je samostatná  
 Serializovaný výstup <xref:System.Windows.Markup.XamlWriter.Save%2A> je samostatný; vše, co je serializováno, je obsaženo uvnitř [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jedné stránky s jedním kořenovým prvkem a bez externích odkazů kromě identifikátorů URI. Například pokud vaše stránka odkazuje prostředky z prostředků aplikace, budou tyto zobrazí, jako by byly součástí stránky, které jsou serializovány.  
  
<a name="Extension_References_are_Dereferenced"></a>
## <a name="extension-references-are-dereferenced"></a>Odkazy na rozšíření jsou odkazovány  
 Běžné odkazy na objekty provedené různými formáty `StaticResource` rozšíření `Binding`značek, například nebo , budou procesem serializace odkazovány. Ty byly již dereferenced v době, kdy byly vytvořeny objekty <xref:System.Windows.Markup.XamlWriter.Save%2A> v paměti v běhu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikace a logika není znovu původní obnovit tyto odkazy na serializované výstupu. To potenciálně zamrzne všechny databound nebo zdroj získané hodnoty, které mají být hodnota naposledy používá reprezentace za běhu, pouze omezené nebo nepřímé schopnost i odlišit tuto hodnotu od jakékoli jiné hodnoty nastavené místně. Obrázky jsou také serializovány jako odkazy na objekty, které existují v projektu, nikoli jako původní zdrojové odkazy, a ztrácejí bez ohledu na název souboru nebo identifikátor URI, na který bylo původně odkazováno. I prostředky deklarované na stejné stránce jsou vidět serializovány do bodu, kde byly odkazovány, spíše než jsou zachovány jako klíč kolekce prostředků.  
  
<a name="Event_Handling_is_Not_Preserved"></a>
## <a name="event-handling-is-not-preserved"></a>Zpracování událostí není zachováno.  
 Při obslužné [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] rutiny událostí, které jsou přidány prostřednictvím jsou serializovány, nejsou zachovány. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]bez kódu na pozadí (a také bez související x:Code mechanismus) nemá žádný způsob serializace runtime procedurální logiky. Vzhledem k tomu, že serializace je samostatná a omezena na logický strom, neexistuje žádné zařízení pro ukládání obslužné rutiny událostí. V důsledku toho jsou z výstupu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]odebrány atributy obslužné rutiny události, samotnéatributy i hodnota řetězce, která pojmenovává obslužnou rutinu .  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Realistické scénáře pro použití XAMLWriter.Save  
 Zatímco omezení zde uvedené jsou poměrně podstatné, stále existuje <xref:System.Windows.Markup.XamlWriter.Save%2A> několik vhodných scénářů pro použití pro serializaci.  
  
- Vektorový nebo grafický výstup: Výstup vykreslené oblasti lze použít k reprodukci stejného vektoru nebo grafiky při opětovném načtení.  
  
- Dokumenty s formátovaným textem a tokem: Text a veškeré formátování prvků a uzavření prvků v něm jsou zachovány ve výstupu. To může být užitečné pro mechanismy, které přibližné funkce schránky.  
  
- Zachování dat obchodních objektů: Pokud máte uložená data ve vlastních prvcích, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jako jsou data XML, tak dlouho, dokud vaše obchodní objekty dodržovat základní pravidla, jako je poskytování vlastníkonstruktory a převod pro hodnoty vlastností odkazem, tyto obchodní objekty mohou být zachovány prostřednictvím serializace.
