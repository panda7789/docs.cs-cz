---
title: Omezení serializace XamlWriter.Save
ms.date: 03/30/2017
helpviewer_keywords:
- XamlWriter.Save [WPF], serialization limitations of
- limitations of XamlWriter.Save
- serialization limitations of XamlWriter.Save
ms.assetid: f86acc91-2b67-4039-8555-505734491d36
ms.openlocfilehash: 5b9141d5df40d74c4682f418a8fb089fddcfcaa9
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740750"
---
# <a name="serialization-limitations-of-xamlwritersave"></a>Omezení serializace XamlWriter.Save
Rozhraní API <xref:System.Windows.Markup.XamlWriter.Save%2A> lze použít k serializaci obsahu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace jako [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru. Existují však významná omezení přesně toho, co je serializováno. Tato omezení a některé obecné otázky jsou popsány v tomto tématu.  

<a name="Run_Time__Not_Design_Time_Representation"></a>   
## <a name="run-time-not-design-time-representation"></a>Reprezentace za běhu, nikoli při návrhu  
 Základní filozofie, co je serializován voláním <xref:System.Windows.Markup.XamlWriter.Save%2A>, je, že výsledkem bude reprezentace objektu, který je serializován, za běhu. Mnoho vlastností návrhu původního [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] souboru již může být optimalizováno nebo ztraceno v době, kdy je [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] načten jako objekty v paměti, a při volání <xref:System.Windows.Markup.XamlWriter.Save%2A> k serializaci nejsou zachovány. Serializovaným výsledkem je efektivní reprezentace vytvořeného logického stromu aplikace, ale ne nutně původní [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], která ho vytvořila. Tyto problémy usnadňují použití serializace <xref:System.Windows.Markup.XamlWriter.Save%2A> v rámci rozsáhlé [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] návrhové plochy.  
  
<a name="Serialization_is_Self_Contained"></a>   
## <a name="serialization-is-self-contained"></a>Serializace je samostatně obsažena.  
 Serializovaný výstup <xref:System.Windows.Markup.XamlWriter.Save%2A> je uložený jako samostatný; vše, co je serializován, je obsaženo uvnitř [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] jedné stránky s jedním kořenovým elementem a žádné externí odkazy Kromě identifikátorů URI. Například pokud vaše stránka odkazovala na prostředky z prostředků aplikace, zobrazí se jako součást serializované stránky.  
  
<a name="Extension_References_are_Dereferenced"></a>   
## <a name="extension-references-are-dereferenced"></a>Odkazy na rozšíření se odkazují  
 Běžné odkazy na objekty vytvořené pomocí různých formátů rozšíření značek, jako je například `StaticResource` nebo `Binding`, budou na základě procesu serializace odkážené. V době, kdy byly objekty v paměti vytvořeny modulem runtime aplikace, již byly odstraněné, a logika <xref:System.Windows.Markup.XamlWriter.Save%2A> nepřejde k původnímu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], aby obnovila takové odkazy na serializovaný výstup. Tím se potenciálně zablokuje jakákoli hodnota získaná pomocí databoundu nebo prostředku, která se může vyhodnotit jako naposledy použité v běhu, a to s omezenou nebo nepřímou schopností odlišit takovou hodnotu z jakékoli jiné hodnoty v místním nastavení. Bitové kopie jsou také serializovány jako odkazy na objekty pro obrázky, které v projektu existují, a nikoli jako původní odkazy na zdrojový soubor nebo identifikátor URI, který byl původně odkazován. Prostředky deklarované na stejné stránce se zobrazí serializované do místa, kde byly odkazovány, místo toho, aby byly zachovány jako klíč kolekce prostředků.  
  
<a name="Event_Handling_is_Not_Preserved"></a>   
## <a name="event-handling-is-not-preserved"></a>Zpracování událostí není zachováno.  
 Pokud jsou obslužné rutiny událostí přidávané prostřednictvím [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] serializovány, nejsou zachovány. [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bez kódu na pozadí (a také bez souvisejícího mechanismu x:Code) nemá žádný způsob serializace běhové procesní logiky. Protože serializace je samostatně obsažena a omezena na logický strom, neexistuje žádné zařízení pro ukládání obslužných rutin událostí. V důsledku toho jsou z výstupního [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]odebrány atributy obslužné rutiny události, samotný atribut a řetězcová hodnota, která má název obslužné rutiny.  
  
<a name="Realistic_Scenarios_for_Use_of_XAMLWriter_Save"></a>   
## <a name="realistic-scenarios-for-use-of-xamlwritersave"></a>Reálné scénáře pro použití XAMLWriter. Save  
 I když jsou uvedená omezení poměrně podstatná, je stále k dispozici několik vhodných scénářů pro použití <xref:System.Windows.Markup.XamlWriter.Save%2A> pro serializaci.  
  
- Vektorový nebo grafický výstup: výstup vykreslené oblasti lze použít k reprodukci stejného vektoru nebo grafiky při opětovném načtení.  
  
- Rich Text a flow Documents: text a všechny formátování elementů a element v něm obsažené jsou zachovány ve výstupu. To může být užitečné pro mechanismy, které mají přibližnou funkčnost schránky.  
  
- Zachování dat obchodních objektů: Pokud máte uložená data ve vlastních prvcích, jako jsou data XML, tak dlouho, jak vaše obchodní objekty následují základní pravidla [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jako je poskytování vlastních konstruktorů a převod hodnot vlastností podle odkazu, tyto firmy objekty mohou být perpetuated prostřednictvím serializace.
