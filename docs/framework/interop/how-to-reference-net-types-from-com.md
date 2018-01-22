---
title: "Postupy: Odkazování na typy .NET z modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b452dd686286ba0ddf648ee532e67a0c121f66eb
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-reference-net-types-from-com"></a>Postupy: Odkazování na typy .NET z modelu COM
Z hlediska kódu klienta a serveru jsou rozdíly mezi modelem COM a rozhraním .NET Framework z velké části nepostřehnutelné. Klienti aplikace Microsoft Visual Basic mohou zobrazovat objekt rozhraní .NET v prohlížeči objektů, který vystavuje metody objektu a syntaxi, vlastnosti a pole přesně tak, jako by se jednalo o jakýkoli jiný objekt modelu COM.  
  
 Proces importování knihovny typů je v případě klientů jazyka C++ poněkud složitější, ačkoli se pro exportování metadat do knihovny typů COM používají stejné nástroje. Chcete-li objekt členy rozhraní .NET z nespravovaného klienta C++, odkaz na soubor TLB (vytvořeného s Tlbexp.exe) s **#import** – direktiva. Při odkazování na knihovny typů z jazyka C++, musíte buď zadat **raw_interfaces_only –** možnost nebo import definice v základní knihovně tříd, Mscorlib.tlb.  
  
### <a name="to-import-a-library"></a>Postup importování knihovny  
  
-   Zadejte **raw_interfaces_only –** možnost **#import** – direktiva. Příklad:  
  
    ```cpp  
    #import "..\LoanLib\LoanLib.tlb" raw_interfaces_only  
    ```  
  
     -nebo-  
  
-   Zadejte také direktivu #import pro knihovnu Mscorlib.tlb. Příklad:  
  
    ```cpp  
    #import "mscorlib.tlb"  
    #import "..\LoanLib\LoanLib.tlb"  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Vystavení komponent architektury .NET Framework pro COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Registrování sestav pomocí modelu COM](../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Volání metody objekt .NET.](http://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [Nasazení aplikace pro přístup COM](http://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce)
