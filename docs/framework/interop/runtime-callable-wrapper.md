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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a4a2f59ee81ac7884050f588d9bd437977490e9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210129"
---
# <a name="runtime-callable-wrapper"></a>Obálka volatelná za běhu
Modul common language runtime poskytuje objekty modelu COM přes proxy server volá obálka volatelná za běhu (RCW). I když objekt RCW se zdá být běžný objekt pro klienty .NET, jeho primární funkce je zařadit volání mezi klient .NET a COM objekty.  
  
 Modul runtime vytvoří přesně jeden objekt RCW pro každý objekt modelu COM, bez ohledu na počet odkazů, které existují k tomuto objektu. Modul runtime udržuje jeden objekt RCW proces pro každý objekt.  Pokud vytvoříte obálky RCW v jedné doméně aplikace nebo objektu apartment a pak předejte odkaz na další aplikační domény nebo objektu apartment, proxy první objekt, který se použije.  Jak ukazuje následující obrázek, může obsahovat libovolný počet spravovaných klientů odkaz na objekty modelu COM, které zveřejňují rozhraní INew a INewer.  

Následující obrázek znázorňuje proces pro získání přístupu k objektům modelu COM pomocí obálka volatelná za běhu:

 ![Proces pro přístup k modelu COM objekty throug RCW.](./media/runtime-callable-wrapper/runtime-callable-wrapper.gif)  

 Používání metadat odvozený z knihovny typů, modul runtime vytvoří volaný objekt modelu COM a obálku pro daný objekt. Každý objekt RCW udržuje mezipaměť ukazatele rozhraní na objekt COM, se zabalí a uvolní svůj odkaz na objekt modelu COM, pokud objekt RCW je už nepotřebujete. Modul runtime provádí uvolňování paměti RCW.  
  
 Mezi ostatní aktivity zařadí RCW dat mezi spravovaným a nespravovaným kódem jménem zabaleného objektu. Konkrétně objekt RCW poskytuje zařazování pro argumenty metody a vrácené hodnoty metody pokaždé, když se klient a server mají odlišné reprezentace dat předávaných mezi nimi.  
  
 Standardní obálky vynucuje integrované zařazování pravidla. Když klient .NET předá jako součást argumentu typu řetězec neřízeným objektem, obálku převede řetězec na typ BSTR. Volající by měl vrátit objekt modelu COM BSTR spravované volajícímu, přijímá řetězec. Klient i server odesílat a přijímat data, která je pro jejich srozumitelná. Jiné typy vyžadují žádný převod. Například standardní obálky vždycky předá 4bajtové celé číslo mezi spravovaným a nespravovaným kódem bez převodu typu.  
  
## <a name="marshaling-selected-interfaces"></a>Zařazování vybraných rozhraní  
 Hlavním cílem [obálka volatelná za běhu](runtime-callable-wrapper.md) (RCW), je skrýt rozdíly mezi spravovanými a nespravovanými programovacích modelů. Vytvořit jednoduchý přechod obálky RCW využívá vybrané rozhraní modelu COM bez vystavení klientovi .NET, jak je znázorněno na následujícím obrázku. 

 Následující obrázek ukazuje rozhraní COM a obálka volatelná za běhu: 
  
 ![Snímek obrazovky obálka volatelná za běhu pomocí rozhraní.](./media/runtime-callable-wrapper/runtime-callable-wrapper-interfaces.gif)  
  
 Po vytvoření jako objekt časné vazby Obálka RCW je určitého typu. Implementuje rozhraní, že objekt modelu COM implementuje a zveřejňuje metody, vlastnosti a události z rozhraní objektu. Na obrázku RCW zpřístupňuje rozhraní INew ale spotřebovává **IUnknown** a **IDispatch** rozhraní. Dále RCW zpřístupňuje všechny členy rozhraní INew na klienta rozhraní .NET.  
  
 Objekt RCW využívá rozhraní uvedené v následující tabulce, které jsou zveřejněné v objektu, který ho zalamoval.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|**IDispatch**|Pozdní vazba modelu COM objektů prostřednictvím reflexe.|  
|**IErrorInfo**|Poskytuje textový popis chyby, její zdroj, soubor nápovědy, kontextové nápovědy a identifikátor GUID rozhraní definované chyba (vždy **GUID_NULL** pro třídy .NET).|  
|**IProvideClassInfo**|Pokud je objekt modelu COM zabalené implementuje **iprovideclassinfo –**, Objekt RCW extrahuje informace o typu z tohoto rozhraní poskytovat lepší typu identitu.|  
|**IUnknown**|Pro objekt identit, převod typu a správa životního cyklu:<br /><br /> – Identity objekt<br />     Modul runtime rozlišuje mezi objekty modelu COM porovnáním hodnoty **IUnknown** rozhraní pro každý objekt.<br />– Vynucení typ<br />     Objekt RCW rozpozná zjišťování dynamického typu prováděné **QueryInterface** metody.<br />-Správa životního cyklu<br />     Použití **QueryInterface** metody RCW získá a uchovává odkaz na objekt v nespravované dlouho, dokud modul runtime provádí uvolňování paměti na obálku, který uvolní nespravované objektu.|  
  
 Objekt RCW volitelně využívá rozhraní uvedené v následující tabulce, které jsou zveřejněné v objektu, který ho zalamoval.  
  
|Rozhraní|Popis|  
|---------------|-----------------|  
|**IConnectionPoint** a **IConnectionPointContainer**|Převede objekty obálky RCW, která zpřístupňují spojovací bod styl události na základě delegáta události.|  
|**Rozhraní IDispatchEx**|Pokud třída implementuje **rozhraní IDispatchEx**, implementuje RCW **IExpando**. **Rozhraní IDispatchEx** rozhraní je rozšířením **IDispatch** rozhraní, na rozdíl od **IDispatch**, umožňuje výčtu, přidání, odstranění a malá a velká písmena volání členů.|  
|**IEnumVARIANT**|Umožňuje typy modelu COM, které podporují výčty jsou považovány za kolekce.|  
  
## <a name="see-also"></a>Viz také:

- [COM – obálky](com-wrappers.md)
- [Obálka volatelná aplikacemi COM](com-callable-wrapper.md)
- [Souhrn převodu sestavení knihovny typů na](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/k83zzh38(v=vs.100))
- [Import knihovny typů ve formě sestavení](importing-a-type-library-as-an-assembly.md)
