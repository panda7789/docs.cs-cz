---
title: Izolace sítě pro aplikace z obchodu Microsoft Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 390a0281f03b08322cc1bee469b601fd5a1547c4
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802161"
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolace sítě pro aplikace z obchodu Microsoft Store

Třídy v oborech názvů <xref:System.Net>, <xref:System.Net.Http>a <xref:System.Net.Http.Headers> lze použít k vývoji aplikací pro Windows Store nebo aplikací klasické pracovní plochy. Při použití v aplikaci pro Windows Store jsou třídy v těchto oborech názvů ovlivněny izolací sítě, což je součást modelu zabezpečení aplikace, kterou používá systém Windows 8. V manifestu aplikace musí být povoleny vhodné síťové funkce pro aplikaci pro Windows Store, aby mohl systém povolit přístup k síti.  
  
## <a name="checklist-for-network-isolation"></a>Kontrolní seznam pro izolaci sítě  

Pomocí tohoto kontrolního seznamu se ujistěte, že je pro vaši aplikaci pro Windows Store nakonfigurovaná izolace sítě.  
  
1. Určete směr požadavků na přístup k síti, které aplikace potřebuje. Může to být buď odchozí požadavky iniciované klientem, nebo příchozí nevyžádaný požadavek, nebo může být kombinací obou těchto typů síťových požadavků.  
  
2. Určete typ síťových prostředků, se kterými bude aplikace komunikovat. Aplikace může vyžadovat komunikaci s důvěryhodnými prostředky v domácí nebo pracovní síti. Aplikace může vyžadovat komunikaci s prostředky na internetu. Aplikace může potřebovat přístup k oběma typům síťových prostředků.  
  
3. Nakonfigurujte možnosti izolace sítě, které jsou v manifestu aplikace minimální a požadované.  
  
4. Nasaďte a spusťte aplikaci pro testování pomocí nástrojů pro izolaci sítě, které jsou k dispozici pro řešení potíží.  
  
Podrobnější informace o tom, jak nakonfigurovat možnosti sítě a nástroje pro izolaci používané pro řešení potíží s izolací sítě, najdete v tématu [Konfigurace možností izolace sítě](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10)) v dokumentaci pro vývojáře Windows 8. x Store.
  
## <a name="see-also"></a>Viz také:

- [Připojení k webové službě](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Pokyny a kontrolní seznam pro izolaci sítě](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Rychlý Start: připojení pomocí HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [Jak používat obslužné rutiny HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [Jak zabezpečit připojení HttpClient](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [Ukázka HttpClient](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
