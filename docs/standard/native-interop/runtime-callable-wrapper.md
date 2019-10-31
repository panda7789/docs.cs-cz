---
title: Obálka volatelná za běhu
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, COM wrappers
- RCW
- COM wrappers
- runtime callable wrappers
- interoperation with unmanaged code, COM wrappers
ms.assetid: 7e542583-1e31-4e10-b523-8cf2f29cb4a4
ms.openlocfilehash: 70ed4176872e18ccafa00808630fcc51337b8479
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123215"
---
# <a name="runtime-callable-wrapper"></a>Obálka volatelná za běhu
Modul CLR (Common Language Runtime) zpřístupňuje objekty COM prostřednictvím proxy s názvem obálka s voláním za běhu (RCW). I když se RCW jeví jako běžný objekt pro klienty rozhraní .NET, jeho primární funkce je zařazování volání mezi klientem rozhraní .NET a objektem COM.  
  
 Modul runtime vytváří přesně jeden RCW pro každý objekt modelu COM, bez ohledu na počet odkazů, které existují na daném objektu. Modul runtime udržuje jeden RCW na proces pro každý objekt.  Pokud vytvoříte RCW v jedné doméně aplikace nebo objektu apartment a potom předáte odkaz na jinou doménu aplikace nebo objekt Apartment, bude použit proxy server k prvnímu objektu.  Jak ukazuje následující obrázek, libovolný počet spravovaných klientů může obsahovat odkaz na objekty modelu COM, které zveřejňují rozhraní INew a INewer.  

Následující obrázek znázorňuje proces pro přístup k objektům modelu COM prostřednictvím obálky s možností přístupu za běhu:

 ![Proces pro přístup k objektům COM přes RCW.](./media/runtime-callable-wrapper/runtime-callable-wrapper.gif)  

 Pomocí metadat odvozených z knihovny typů vytvoří modul runtime objekt COM, který je volán, a obal pro daný objekt. Každý RCW udržuje mezipaměť ukazatelů rozhraní u objektu COM, který zabalí a uvolní svůj odkaz na objekt modelu COM, pokud RCW již není potřeba. Modul runtime provádí uvolňování paměti v RCW.  
  
 Mimo jiné činnosti RCW zařazování dat mezi spravovaným a nespravovaným kódem jménem zabaleného objektu. Konkrétně RCW poskytuje zařazování pro argumenty metody a návratové hodnoty metody pokaždé, když klient a Server mají různá reprezentace dat předaná mezi nimi.  
  
 Standardní obálka vynutila Vestavěná pravidla zařazování. Například když klient rozhraní .NET předává jako součást argumentu nespravovanému objektu typ String, obálka převede řetězec na typ BSTR. Pokud objekt COM vrátí BSTR ke svému spravovanému volajícímu, volající obdrží řetězec. Jak klient, tak server odesílají a přijímají data, která jsou pro ně známa. Jiné typy nevyžadují konverzi. Například standardní obálka vždy předá celé 4 bajty mezi spravovaným a nespravovaným kódem bez převodu typu.  
  
## <a name="marshaling-selected-interfaces"></a>Zařazování vybraných rozhraní  
 Primárním cílem obálky s vyRCWelné [za běhu](runtime-callable-wrapper.md) je skrýt rozdíly mezi spravovanými a nespravovanými programovacími modely. Pro vytvoření bezproblémového přechodu RCW spotřebovává vybraná rozhraní COM bez jejich zveřejnění klientovi .NET, jak je znázorněno na následujícím obrázku. 

 Následující obrázek ukazuje rozhraní COM a obálku s možností spuštění za běhu: 
  
 ![Snímek obrazovky s vydanou obálkou za běhu s rozhraními](./media/runtime-callable-wrapper/runtime-callable-wrapper-interfaces.gif)  
  
 Při vytvoření jako objektu s časnou vazbou je RCW konkrétním typem. Implementuje rozhraní, která objekt COM implementuje a zpřístupňuje metody, vlastnosti a události z rozhraní objektu. Na ilustraci RCW zpřístupňuje rozhraní INew, ale spotřebovává rozhraní **IUnknown** a **IDispatch** . Kromě toho RCW zpřístupňuje všechny členy rozhraní INew klientovi .NET.  
  
 RCW spotřebovává rozhraní uvedená v následující tabulce, která jsou zpřístupněna objektem, který balí.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|**IDispatch**|Pro pozdní vazbu k objektům modelu COM prostřednictvím reflexe.|  
|**IErrorInfo**|Poskytuje textový popis chyby, její zdroj, soubor s nápovědu, kontext nápovědu a identifikátor GUID rozhraní, které definuje chybu (vždy **GUID_NULL** pro třídy .NET).|  
|**IProvideClassInfo**|Pokud objekt modelu COM, který je zabalen, implementuje **IProvideClassInfo**, RCW extrahuje informace o typu z tohoto rozhraní za účelem poskytnutí lepší identity typu.|  
|**IUnknown**|V případě identity objektu zadejte vynucení a správu životnosti:<br /><br /> – Identita objektu<br />     Modul runtime rozlišuje objekty modelu COM porovnáním hodnoty rozhraní **IUnknown** pro každý objekt.<br />-Typ – konverze<br />     RCW rozpoznává zjišťování dynamického typu prováděného metodou **QueryInterface** .<br />– Správa životního cyklu<br />     Pomocí metody **QueryInterface** získá RCW a obsahuje odkaz na nespravovaný objekt, dokud modul runtime neprovede uvolňování paměti na obálce, což uvolní nespravovaný objekt.|  
  
 RCW volitelně spotřebovává rozhraní uvedená v následující tabulce, které jsou zpřístupněny objektem, který balí.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|**IConnectionPoint** a **IConnectionPointContainer**|RCW převede objekty, které zpřístupňují styl události spojovacího bodu, na události založené na delegování.|  
|**IDispatchEx –** (pouze .NET Framework) |Pokud třída implementuje **IDispatchEx –** , RCW implementuje **IExpando**. Rozhraní **IDispatchEx –** je rozšíření rozhraní **IDispatch** , které na rozdíl od rozhraní **IDispatch**povoluje vyčíslení, sčítání, odstraňování a rozlišování velkých a malých písmen členů.|  
|**IEnumVARIANT**|Povoluje, aby typy COM, které podporují výčty, byly zpracovány jako kolekce.|  
  
## <a name="see-also"></a>Viz také:

- [COM – obálky](com-wrappers.md)
- [Obálka volatelná aplikacemi COM](com-callable-wrapper.md)
- [Souhrn převodu knihovny typů na sestavení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Import knihovny typů ve formě sestavení](../../framework/interop/importing-a-type-library-as-an-assembly.md)
