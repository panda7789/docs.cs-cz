---
title: Izolace sítě pro aplikace z obchodu Microsoft Store
ms.date: 03/30/2017
ms.assetid: b064497c-d956-46b8-838d-7a0223c7e200
ms.openlocfilehash: cb6dc6e3bede88cc6b33632d7fc8f6f19034a9c1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190259"
---
# <a name="network-isolation-for-windows-store-apps"></a>Izolace sítě pro aplikace z obchodu Microsoft Store
Třídy v <xref:System.Net>, <xref:System.Net.Http>, a <xref:System.Net.Http.Headers> obory názvů slouží k vývoji aplikací Windows Store a desktopové aplikace. Při použití v aplikaci Windows Store, třídy v těchto oborech názvů jsou ovlivněny izolace sítě, součástí modelu zabezpečení aplikace používané [!INCLUDE[win8](../../../includes/win8-md.md)]. Musí být povoleno příslušné síťové funkce v manifestu aplikace pro Windows Store aplikaci pro systém umožňující přístup k síti.  
  
## <a name="checklist-for-network-isolation"></a>Kontrolní seznam pro izolaci sítě  
 Kontrolní seznam použijte, abyste měli jistotu, že izolace sítě je nakonfigurován pro aplikace pro Windows Store.  
  
1.  Určení směru síťové požadavky na přístup potřebné aplikace. To může být odchozích požadavků klientem iniciované nebo nevyžádaná příchozí požadavky nebo může být kombinaci těchto typů požadavku sítě.  
  
2.  Určete typ síťové prostředky, které aplikace budou komunikovat s. Aplikace může potřebovat komunikovat s důvěryhodným prostředky v síti domácí nebo pracovní. Aplikace může být nutné pro komunikaci s prostředky v síti Internet. Aplikace může potřebovat přístup na oba typy síťových prostředků.  
  
3.  Konfigurace možností sítě minimální požadovanou izolaci v manifestu aplikace.  
  
4.  Nasazení a spuštění aplikace a otestovat ho pomocí nástrojů izolace sítě pro řešení potíží.  
  
 Podrobnější informace o tom, jak nakonfigurovat síťové funkce a nástroje pro izolaci používají k řešení potíží izolace sítě najdete v tématu [konfiguraci schopnosti izolace sítě](https://go.microsoft.com/fwlink/?LinkID=228265) v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] pro vývojáře dokumentace ke službě.  
  
## <a name="see-also"></a>Viz také:

- [Připojení k webové službě](https://go.microsoft.com/fwlink/?LinkID=245696)
- [Pokyny a kontrolní seznam pro izolaci sítě](https://go.microsoft.com/fwlink/?LinkID=228265)
- [Rychlý start: Připojení pomocí položky HttpClient](https://go.microsoft.com/fwlink/?LinkId=245697)
- [Jak používat HttpClient obslužné rutiny](https://go.microsoft.com/fwlink/?LinkId=245699)
- [Jak zabezpečit HttpClient připojení](https://go.microsoft.com/fwlink/?LinkId=245698)
- [Ukázka třídy HttpClient](https://go.microsoft.com/fwlink/?LinkId=242550)
