---
title: Konvence schématu konfigurace WIF
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: 39ed32bb7e926f275e996b09e746c879c6d3fe9e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120871"
---
# <a name="wif-configuration-schema-conventions"></a>Konvence schématu konfigurace WIF
Toto téma popisuje konvence používaný v celém témata týkající se konfigurace technologie Windows Identity Foundation (WIF) a popisuje některé běžné funkce a atributy se používají v [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) a [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) oddíly.  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Režimy  
 Mnoho elementů konfigurace technologie WIF má `mode` atribut. Tento atribut se obvykle řídí, které třída se používá k provést určitou část zpracování a prvky konfigurace, které jsou povoleny jako podřízené prvky aktuálního prvku. Chyba konfigurace bude vyvolána, pokud jsou prvky, které jsou zahrnuty v konfiguračním souboru ignoruje kvůli nastavení režimu.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>Hodnoty TimeSpan  
 Kde <xref:System.TimeSpan> je použít jako typ atributu, najdete v článku <xref:System.TimeSpan.Parse%28System.String%29> metoda zobrazíte povolený formát. Tento formát odpovídá specifikaci následující.  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 Například "30", "30.00:00", "30.00:00:00" všechny znamená 30 dní; a "00:05", "00: 05:00", "0.00:05:00.00" všechny znamená 5 minut.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Odkazy na certifikáty  
 Odkazy na certifikáty pomocí trvat několik elementů `<certificateReference>` elementu. Při odkazování na certifikát, jsou k dispozici následující atributy.  
  
|||  
|-|-|  
|`storeLocation`|Hodnota <xref:System.Security.Cryptography.X509Certificates.StoreLocation> výčet: `CurrentUser` nebo `CurrentMachine`.|  
|`storeName`|Hodnota <xref:System.Security.Cryptography.X509Certificates.StoreName> výčet; zvláště užitečná pro tento kontext jsou `My` a `TrustedPeople`.|  
|`x509FindType`|Hodnota <xref:System.Security.Cryptography.X509Certificates.X509FindType> výčet; zvláště užitečná pro tento kontext jsou `FindBySubjectName` a `FindByThumbprint`. Eliminovat riziko chyb, se doporučuje, který `FindByThumbprint` typ použít v produkčním prostředí.|  
|`findValue`|Hodnota použitá k vyhledání certifikátu, na základě `x509FindType` atribut. Eliminovat riziko chyb, se doporučuje, který `FindByThumbprint` typ použít v produkčním prostředí. Když `FindByThumbPrint` není zadána, tento atribut má hodnotu, která je formulář šestnáctkový řetězec certifikátu kryptografický otisk, například "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Odkazy na vlastní typ.  
 Referenční dokumentace několik elementů vlastních typů pomocí `type` atribut. Tento atribut by měl zadejte název vlastního typu. Chcete-li odkazovat na typ z globální mezipaměti sestavení (GAC), by měla sloužit silným názvem. K odkazování typu ze sestavení v přihrádce / directory, může použít jednoduchý odkaz na kvalifikovaný pro sestavení. Typy definované v App_Code / directory může odkazovat také jednoduše zadáním názvu typu se žádné opravňující sestavení.  
  
 Vlastní typy musí být odvozen od typu určeného a musí zadat `public` výchozího konstruktoru (0 argumentů).  
  
## <a name="see-also"></a>Viz také:

- [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)
- [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
