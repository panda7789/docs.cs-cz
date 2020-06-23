---
title: 'Postupy: Načtení kryptografického otisku certifikátu'
description: Naučte se, jak zadat deklarace identity nalezené v certifikátu X. 509, který je nezbytný při vývoji aplikace WCF, která používá certifikáty pro ověřování.
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: 87c696323af442021af267f0d8c523418e2234f7
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246776"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Postupy: Načtení kryptografického otisku certifikátu
Při psaní aplikace Windows Communication Foundation (WCF), která pro ověřování používá certifikát X. 509, je často nutné zadat deklarace identity nalezené v certifikátu. Například při použití výčtu v metodě je třeba uvést deklaraci identity kryptografického otisku <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> . Hledání hodnoty deklarace identity vyžaduje dva kroky. Nejprve otevřete modul snap-in konzoly Microsoft Management Console (MMC) pro certifikáty. (Viz [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md).) Za druhé, jak je popsáno zde, najděte příslušný certifikát a zkopírujte jeho kryptografický otisk (nebo jiné hodnoty deklarace identity).  
  
 Pokud používáte certifikát pro ověřování služby, je důležité poznamenat hodnotu sloupce **Vystaveno pro** (první sloupec v konzole). Při použití SSL (Secure Sockets Layer) (SSL) jako zabezpečení přenosu provede jedna z prvních kontrol k porovnání základní adresy identifikátoru URI (Uniform Resource Identifier) služby s hodnotou **vydanou** hodnotou. Hodnoty se musí shodovat nebo se proces ověřování zastaví.  
  
 K vytváření dočasných certifikátů pro použití pouze během vývoje můžete použít také rutinu PowerShellu New-SelfSignedCertificate. Ve výchozím nastavení se ale takový certifikát nevydá certifikační autorita a nedá se použít pro produkční účely. Další informace najdete v tématu [Postup: vytváření dočasných certifikátů pro použití během vývoje](how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Načtení kryptografického otisku certifikátu  
  
1. Otevřete modul snap-in konzoly MMC (Microsoft Management Console) pro certifikáty. (Viz [Postup: zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2. V levém podokně **kořenového okna konzoly** klikněte na **certifikáty (místní počítač)**.  
  
3. Klikněte na složku **osobní** a rozbalte ji.  
  
4. Klikněte na složku **certifikáty** a rozbalte ji.  
  
5. V seznamu certifikátů si všimněte nadpisu **zamýšleného účelu** . Vyhledejte certifikát, který vypíše **ověřování klienta** jako zamýšlený účel.  
  
6. Dvakrát klikněte na certifikát.  
  
7. V dialogovém okně **certifikát** klikněte na kartu **Podrobnosti** .  
  
8. Procházejte seznamem polí a kliknutím na **kryptografický otisk**.  
  
9. Zkopírujte šestnáctkové znaky z pole. Pokud se tento kryptografický otisk používá v kódu pro `X509FindType` , odeberte mezery mezi hexadecimálními čísly. Například kryptografický otisk "14 33 09 50 2D D8 2a E4 E6 F8 38 86 B0 0d 42 77 a3 2a 7b" by měl být v kódu uveden jako "a909502dd82ae41433e6f83886b00d4277a32a7b".  
  
## <a name="see-also"></a>Viz také

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [Postupy: Konfigurace portu s certifikátem SSL](how-to-configure-a-port-with-an-ssl-certificate.md)
- [Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC](how-to-view-certificates-with-the-mmc-snap-in.md)
- [Postupy: Vytváření dočasných certifikátů pro použití během vývoje](how-to-create-temporary-certificates-for-use-during-development.md)
