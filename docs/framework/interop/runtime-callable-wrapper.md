---
title: "Obálka volatelná za běhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, COM wrappers
- RCW
- COM wrappers
- runtime callable wrappers
- interoperation with unmanaged code, COM wrappers
ms.assetid: 7e542583-1e31-4e10-b523-8cf2f29cb4a4
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 980ed0a10c4e8152da20846710b21c244a341271
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="runtime-callable-wrapper"></a>Obálka volatelná za běhu
Modul common language runtime zpřístupní objektů COM prostřednictvím proxy serveru názvem obálka volatelná za běhu (RCW). I když RCW se zdá být objekt obyčejnou tak, aby klientů .NET, je jeho primární funkce zařazování volání mezi sebou klient .NET a objekt modelu COM.  
  
 Modul runtime vytvoří přesně jeden RCW pro každý objekt modelu COM, bez ohledu na počet odkazů, které existují na tento objekt. Modul runtime udržuje jeden RCW podle procesu pro každý objekt.  Pokud vytvoříte RCW v jedné doméně aplikace nebo typu apartment a pak předejte odkaz na jiné domény aplikace nebo typu apartment, použije se proxy server na první objekt.  Jak ukazuje následující obrázek, může obsahovat libovolný počet spravovaných klientů odkaz na objekty COM, které zveřejňují rozhraní INew a INewer.  
  
 ![RCW](../../../docs/framework/interop/media/rcw.gif "rcw")  
Přístup k objektům modelu COM pomocí obálka volatelná za běhu  
  
 Modul runtime pomocí metadat, které jsou odvozené z knihovny typů, vytvoří objekt COM volané i obálku pro tento objekt. Každý RCW udržuje mezipaměť ukazatele rozhraní na objekt COM se zabalí a uvolní jeho odkaz na objekt COM, když RCW již není potřeba. Modul runtime provádí RCW uvolňování paměti.  
  
 Mimo jiné RCW zařazuje data mezi spravovanými a nespravovanými kódu jménem zabalené objektu. Konkrétně RCW poskytuje zařazování pro argumenty metoda a návratové hodnoty metoda vždy, když klient a server mají různé reprezentace dat předávaných mezi nimi.  
  
 Standardní obálku vynucuje vestavěné zařazování pravidla. Když klient .NET předá typu String jako součást argument objekt nespravované, obálku převede řetězec na typ BSTR. Volající by měl vrátit objekt COM BSTR jeho spravované volajícího, obdrží řetězec. Klient a server odesílat a přijímat data, která je jim dobře známé. Jiné typy vyžadují žádný převod. Například standardní obálku vždycky předá 4bajtový celočíselný mezi spravovanými a nespravovanými kód bez převodu typu.  
  
## <a name="marshaling-selected-interfaces"></a>Zařazování vybrané rozhraní  
 Hlavním cílem, který [obálka volatelná za běhu](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) je skrýt rozdíly mezi spravovanými a nespravovanými programovací modely. Vytvořit snadný přechod, RCW spotřebuje vybrané rozhraní modelu COM bez vystavení je do klienta rozhraní .NET, jak je znázorněno na následujícím obrázku.  
  
 ![RCW s rozhraní](../../../docs/framework/interop/media/rcwwithinterfaces.gif "rcwwithinterfaces")  
Rozhraní COM a obálka volatelná za běhu  
  
 Při vytváření jako objekt časné vazby RCW je konkrétního typu. Implementuje rozhraní implementuje a poskytuje metody, vlastnosti a události z objektu rozhraní COM objektu. Na obrázku RCW zpřístupňuje rozhraní INew ale využívá **IUnknown** a **IDispatch** rozhraní. Navíc RCW zpřístupní všechny členy rozhraní INew klienta rozhraní .NET.  
  
 RCW využívá rozhraní uvedené v následující tabulce, které jsou vystavené objekt, který se zabalí.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|**IDispatch**|Pozdní vazba objekty modelu COM pomocí reflexe.|  
|**IErrorInfo**|Obsahuje textový popis chyby, její zdroj, soubor nápovědy, kontextové nápovědy a identifikátor GUID rozhraní definované chyba (vždy **GUID_NULL** pro rozhraní .NET třídy).|  
|**IProvideClassInfo**|Pokud se objekt COM zabalené implementuje **IProvideClassInfo**, RCW extrahuje informace o typu z tohoto rozhraní poskytovat lepší typ identitu.|  
|**IUnknown**|Pro objekt identitu, převod typu a správu životního cyklu:<br /><br /> – Identity objekt<br />     Modul runtime rozlišuje mezi objekty modelu COM tak, že porovnáte hodnotu **IUnknown** rozhraní pro každý objekt.<br />– Typ převod<br />     RCW rozpozná dynamický typ zjišťování, provádí **QueryInterface** metoda.<br />-Správa životního cyklu<br />     Pomocí **QueryInterface** metodu, RCW získá a obsahuje odkaz na objekt nespravované, dokud modulu runtime provádí obálky, což uvolní nespravované objekt uvolňování paměti.|  
  
 RCW volitelně využívá rozhraní uvedené v následující tabulce, které jsou vystavené objekt, který se zabalí.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|**IConnectionPoint –** a **IConnectionPointContainer**|RCW převede objekty, které zveřejňují styl spojovací bod události na základě delegáta události.|  
|**IDispatchEx**|Pokud třída implementuje **IDispatchEx**, implementuje RCW **IExpando**. **IDispatchEx** rozhraní je rozšířením **IDispatch** rozhraní, na rozdíl od **IDispatch**, umožňuje výčtu, přidání, odstranění a to malá a velká písmena volání metody členů.|  
|**IEnumVARIANT**|Umožňuje typy modelu COM, které podporují výčty jsou považovány za kolekce.|  
  
## <a name="see-also"></a>Viz také  
 [COM – obálky](../../../docs/framework/interop/com-wrappers.md)  
 [Zařazování vybrané rozhraní](http://msdn.microsoft.com/en-us/fdb97fd0-f694-4832-bf15-a4e7cf413840)  
 [Obálka volatelná aplikacemi COM](../../../docs/framework/interop/com-callable-wrapper.md)  
 [Knihovny typů pro souhrn konverze sestavení](http://msdn.microsoft.com/en-us/bf3f90c5-4770-4ab8-895c-3ba1055cc958)  
 [Import knihovny typů jako sestavení](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)
