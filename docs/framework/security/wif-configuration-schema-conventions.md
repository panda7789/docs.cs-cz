---
title: Konvence schématu konfigurace WIF
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: c02d467260a5197cdd01a3819f8a323655a8a08f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045097"
---
# <a name="wif-configuration-schema-conventions"></a>Konvence schématu konfigurace WIF
Toto téma popisuje konvence používané v tématech Konfigurace Windows Identity Foundation (WIF) a popisuje některé běžné funkce a atributy, které se [ \<používají v System. IdentityModel](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) [ \< > a oddíly System. identityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) .  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Druzí  
 Mnoho elementů konfigurace WIF má `mode` atribut. Tento atribut obvykle řídí, která třída se používá k provedení určité části zpracování a které prvky konfigurace jsou povoleny jako podřízené prvky aktuálního prvku. Pokud jsou prvky, které jsou součástí konfiguračního souboru, ignorovány z důvodu nastavení režimu, bude vyvolána chyba konfigurace.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>Hodnoty TimeSpan  
 Kde <xref:System.TimeSpan> je použit jako typ atributu, <xref:System.TimeSpan.Parse%28System.String%29> viz metoda pro zobrazení povoleného formátu. Tento formát odpovídá následující specifikaci.  
  
`[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]`  
  
 Například "30", "30.00:00", "30.00:00:00" všech středních dnů; a "00:05", "00:05:00", "0.00:05:00.00" všechny znamenají 5 minut.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Odkazy na certifikát  
 Několik prvků přebírají odkazy na certifikáty pomocí `<certificateReference>` elementu. Při odkazování na certifikát jsou k dispozici následující atributy.  
  
|||  
|-|-|  
|`storeLocation`|Hodnota <xref:System.Security.Cryptography.X509Certificates.StoreLocation> výčtu: `CurrentUser` nebo. `CurrentMachine`|  
|`storeName`|Hodnota <xref:System.Security.Cryptography.X509Certificates.StoreName> výčtu; nejužitečnější pro tento kontext jsou `My` a `TrustedPeople`.|  
|`x509FindType`|Hodnota <xref:System.Security.Cryptography.X509Certificates.X509FindType> výčtu; nejužitečnější pro tento kontext jsou `FindBySubjectName` a `FindByThumbprint`. Aby nedošlo k chybě, doporučujeme, aby `FindByThumbprint` byl typ použit v produkčním prostředí.|  
|`findValue`|Hodnota použitá k vyhledání certifikátu na základě `x509FindType` atributu. Aby nedošlo k chybě, doporučujeme, aby `FindByThumbprint` byl typ použit v produkčním prostředí. Při `FindByThumbPrint` zadání tohoto atributu převezme hodnota, která je v šestnáctkovém formátu řetězce kryptografického otisku certifikátu; například "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Odkazy na vlastní typ  
 Několik elementů odkazuje na `type` vlastní typy pomocí atributu. Tento atribut by měl určovat název vlastního typu. Chcete-li odkazovat na typ z globální mezipaměti sestavení (GAC), měla by být použita silný název. Chcete-li odkazovat na typ ze sestavení v přihrádce nebo adresáři, lze použít jednoduchý odkaz kvalifikovaný pro sestavení. Typy definované v adresáři App_Code nebo v adresáři mohou být také odkazovány pouhým zadáním názvu typu bez opravňujícího sestavení.  
  
 Vlastní typy musí být odvozeny od zadaného typu a musí poskytovat `public` výchozí konstruktor (0 argument).  
  
## <a name="see-also"></a>Viz také:

- [\<system.identityModel>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)
- [\<system.identityModel.services>](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
