---
title: "WIF konfigurace schématu konvence"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: e327b45ddd260d1a52066b5bf53e7114100ff45c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="wif-configuration-schema-conventions"></a>WIF konfigurace schématu konvence
Toto téma popisuje konvence používaných v celém témata týkající se konfigurace Windows Identity Foundation (WIF) a popisuje některé běžné funkce a atributy se používají v [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) a [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) oddíly.  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Režimy  
 Mnoho konfigurační prvky WIF má `mode` atribut. Obvykle se tento atribut určuje, které třída se používá k provést určitou část zpracování a které konfigurační prvky jsou povoleny jako podřízené prvky aktuálního elementu. Pokud elementy, které jsou zahrnuty v konfiguračním souboru se ignorují kvůli nastavení režimu, bude vyvolána chyba konfigurace.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>Časový interval hodnoty  
 Kde <xref:System.TimeSpan> je použít jako typ atributu, najdete v článku <xref:System.TimeSpan.Parse%28System.String%29> metoda zobrazíte povolené formátu. Tento formát odpovídá specifikaci následující.  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 Například "30", "30.00:00", "30.00:00:00" všechny znamená 30 dní; a "00:05", "00: 05:00", "0.00:05:00.00" všechny znamenat 5 minut.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Odkazy na certifikát  
 Odkazy na certifikáty pomocí trvat několik elementů `<certificateReference>` elementu. Při odkazování na certifikát, jsou k dispozici následující atributy.  
  
|||  
|-|-|  
|`storeLocation`|Hodnota <xref:System.Security.Cryptography.X509Certificates.StoreLocation> výčtu: `CurrentUser` nebo `CurrentMachine`.|  
|`storeName`|Hodnota <xref:System.Security.Cryptography.X509Certificates.StoreName> výčtu; velmi užitečné pro tento kontext se `My` a `TrustedPeople`.|  
|`x509FindType`|Hodnota <xref:System.Security.Cryptography.X509Certificates.X509FindType> výčtu; velmi užitečné pro tento kontext se `FindBySubjectName` a `FindByThumbprint`. Omezit riziko chyby, doporučujeme `FindByThumbprint` typ, který používat v produkčním prostředí.|  
|`findValue`|Hodnota použít k vyhledání certifikátu, založená na `x509FindType` atribut. Omezit riziko chyby, doporučujeme `FindByThumbprint` typ, který používat v produkčním prostředí. Když `FindByThumbPrint` je zadán, přebírá hodnotu, která je hexadecimální řetězec formátu certifikát tento atribut kryptografický otisk, například "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Odkazy na vlastní typ  
 Referenční dokumentace několik elementů vlastních typů pomocí `type` atribut. Tento atribut musí určovat název vlastního typu. Chcete-li typ z globální mezipaměti sestavení (GAC), je třeba použít silným názvem. Chcete-li typu ze sestavení v přihrádce / adresáře, může použít jednoduchý odkaz na sestavení kvalifikovaný. Typy definované v adresáři App_Code nebo adresáře může také odkazovat ze stačí zadat název typu s žádné opravňující sestavení.  
  
 Vlastní typy musí být odvozen od typu určeného a musí zadat `public` výchozí konstruktor (0 argumentů).  
  
## <a name="see-also"></a>Viz také  
 [\<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [\<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
