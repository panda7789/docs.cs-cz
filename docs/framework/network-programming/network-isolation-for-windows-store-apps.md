---
title: Izolace sítě pro aplikace z obchodu Microsoft Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: 390a0281f03b08322cc1bee469b601fd5a1547c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74802161"
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolace sítě pro aplikace z obchodu Microsoft Store

Třídy <xref:System.Net>v <xref:System.Net.Http>, <xref:System.Net.Http.Headers> a jmenné prostory lze použít k vývoji aplikací pro Windows Store nebo desktopových aplikací. Při použití v aplikaci pro Windows Store jsou třídy v těchto oborech názvů ovlivněny izolací sítě, která je součástí modelu zabezpečení aplikace používaného systémem Windows 8. Příslušné síťové funkce musí být povoleny v manifestu aplikace pro aplikaci pro Windows Store, aby systém povolil přístup k síti.  
  
## <a name="checklist-for-network-isolation"></a>Kontrolní seznam pro izolaci sítě  

Pomocí tohoto kontrolního seznamu se ujistěte, že je pro vaši aplikaci pro Windows Store nakonfigurovaná izolace sítě.  
  
1. Určete směr požadavků na přístup k síti, které aplikace potřebuje. Může se jedná o odchozí požadavky iniciované klientem nebo příchozí nevyžádané požadavky nebo může být kombinací obou těchto typů síťových požadavků.  
  
2. Určete typ síťových prostředků, se kterými bude aplikace komunikovat. Aplikace může potřebovat komunikovat s důvěryhodnými prostředky v domácí nebo pracovní síti. Aplikace může potřebovat komunikovat s prostředky na Internetu. Aplikace může potřebovat přístup k oběma typům síťových prostředků.  
  
3. Nakonfigurujte minimální požadované možnosti izolace sítě v manifestu aplikace.  
  
4. Nasaďte a spusťte aplikaci a otestujte ji pomocí nástrojů pro izolaci sítě, které jsou k dispozici pro řešení potíží.  
  
Podrobnější informace o konfiguraci síťových funkcí a nástrojů izolace používaných při řešení potíží s izolací sítě najdete v tématu [Konfigurace možností izolace sítě](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10)) v dokumentaci pro vývojáře windows 8.x Store.
  
## <a name="see-also"></a>Viz také

- [Připojení k webové službě](https://docs.microsoft.com/previous-versions/windows/apps/hh761504(v=win.10))
- [Pokyny a kontrolní seznam pro izolaci sítě](https://docs.microsoft.com/previous-versions/windows/apps/hh770532(v=win.10))
- [Úvodní příručka: Připojení pomocí httpklienta](https://docs.microsoft.com/previous-versions/windows/apps/hh781239(v=win.10))
- [Použití obslužných rutin httpclient](https://docs.microsoft.com/previous-versions/windows/apps/hh781241(v=win.10))
- [Zabezpečení připojení httpclient](https://docs.microsoft.com/previous-versions/windows/apps/hh781240(v=win.10))
- [Ukázka httpklienta](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
