---
title: 'Postupy: Odkazování na typy .NET z modelu COM'
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- importing type library
- COM interop, referencing .NET types
- interoperation with unmanaged code, referencing .NET types
- referencing .NET types
- interoperation with unmanaged code, importing type library
- type libraries
- COM interop, importing type library
ms.assetid: 54917f6f-cb18-4103-b622-856b55da93f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0333cd73240e685b46917d85afe0876532db3fd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391895"
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
 [Vystavení komponent architektury .NET Framework pro COM](exposing-dotnet-components-to-com.md)  
 [Registrování sestav pomocí modelu COM](registering-assemblies-with-com.md)  
 [Volání metody objekt .NET.](https://msdn.microsoft.com/library/40c9626c-aea6-4bad-b8f0-c1de462efd33(v=vs.100))  
 [Nasazení aplikace pro přístup COM](https://msdn.microsoft.com/library/fb63564c-c1b9-4655-a094-a235625882ce(v=vs.100))
