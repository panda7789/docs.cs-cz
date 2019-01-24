---
title: Vystavení komponent architektury .NET Framework pro COM
ms.date: 03/30/2017
helpviewer_keywords:
- exposing .NET Framework components to COM
- interoperation with unmanaged code, exposing .NET Framework components
- COM interop, exposing COM components
ms.assetid: e42a65f7-1e61-411f-b09a-aca1bbce24c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b5c80ba473b0080a1368c82949c765820239ef25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54715735"
---
# <a name="exposing-net-framework-components-to-com"></a>Vystavení komponent architektury .NET Framework pro COM
Zápis typ formátu .NET a použití typu z nespravovaného kódu jsou různé aktivity pro vývojáře. Tato část popisuje několik tipů pro vytváření spravovaného kódu, který spolupracuje s klienty modelu COM:  
  
-   [Kvalifikace typů .NET pro součinnost](../../../docs/framework/interop/qualifying-net-types-for-interoperation.md).  
  
     Všechny spravované typy, metody, vlastnosti, pole a události, které chcete vystavit rozhraní COM musí být veřejné. Typy musí mít veřejný výchozí konstruktor, který je jediný konstruktor, který lze vyvolat pomocí modelu COM.  
  
-   [Použití atributů spolupráce](../../../docs/framework/interop/applying-interop-attributes.md).  
  
     Vlastní atributy v rámci spravovaného kódu můžete vylepšit spolupráci komponenty.  
  
-   [Zabalení sestavení pro model COM](../../../docs/framework/interop/packaging-an-assembly-for-com.md).  
  
     Vývojáři modelu COM může vyžadovat vytvořit souhrn kroky při odkazování na a nasazení vašeho sestavení.  
  
 Kromě toho tato část identifikuje úlohy týkající se používání spravovaného typu z modelu COM klienta.  
  
#### <a name="to-consume-a-managed-type-from-com"></a>Chcete-li využívají spravovaného typu z modelu COM  
  
1.  [Registrace sestavení s modelem COM](../../../docs/framework/interop/registering-assemblies-with-com.md).  
  
     Typy v sestavení (a knihovny typů) musí být zaregistrovaný v době návrhu. Pokud instalační program nezaregistruje sestavení, dáte pokyn, aby vývojářům modelu COM pomocí Regasm.exe.  
  
2.  [Odkazování na typy .NET z modelu COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md).  
  
     Vývojáři modelu COM může odkazovat na typy v sestavení pomocí stejné nástroje a techniky, které jeho tým dnes používá.  
  
3.  [Volání objektu .NET](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100)).  
  
     Vývojáři modelu COM může volat metody u objektu rozhraní .NET stejným způsobem jako volání metody v libovolném nespravovaného typu. Například COM **CoCreateInstance** API aktivuje objektů .NET.  
  
4.  [Nasazení aplikace pro přístup COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100)).  
  
     Sestavení se silným názvem může být nainstalována v globální mezipaměti sestavení a vyžaduje podpis od vydavatele. Sestavení, která nejsou silný název musí být nainstalována v adresáři aplikace klienta.  
  
## <a name="see-also"></a>Viz také:
- [Spolupráce s nespravovaným kódem](../../../docs/framework/interop/index.md)
- [Ukázka zprostředkovatele s objekty COM: Klient COM a .NET Server](../../../docs/framework/interop/com-interop-sample-com-client-and-net-server.md)
