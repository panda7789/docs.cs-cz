---
title: 'Postupy: Načtení kryptografického otisku certifikátu'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: 51debbbcfec2fd5b82460e1dd1d6ece8e77bfc13
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000776"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Postupy: Načtení kryptografického otisku certifikátu
Při psaní aplikace Windows Communication Foundation (WCF), která používá certifikát X.509 pro ověřování, je často nutné zadat deklarací identity najdete v certifikátu. Například musíte zadat kryptografický otisk deklaraci identity při použití <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> výčtu v <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody. Vyhledání hodnoty deklarace identity sestává ze dvou kroků. Nejprve otevřete modul snap-in Certifikáty konzoly Microsoft Management Console (MMC). (Viz [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Za druhé jak je zde popsáno, vyhledejte příslušný certifikát a zkopírujte jeho kryptografický otisk (nebo jiné hodnoty deklarace identity).  
  
 Pokud používáte certifikát pro ověřování služby, je důležité si poznamenejte hodnotu **vystaveno pro** sloupec (první sloupec v konzole). Při použití vrstvy SSL (Secure Sockets), jako je zabezpečení přenosu, jeden z nejprve zkontroluje provádí porovnání základní adresu identifikátoru URI (Uniform Resource) služby **vystaveno pro** hodnotu. Hodnoty musí odpovídat nebo zastavení procesu ověřování.  
  
 Můžete také použít rutinu Powershellu New-SelfSignedCertificate k vytváření dočasných certifikátů pro použití pouze během vývoje. Ve výchozím nastavení ale tento certifikát není vydaný certifikační autoritou a se nedá použít pro produkční účely. Další informace najdete v tématu [jak: Vytváření dočasných certifikátů pro použití během vývoje](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>K načtení kryptografického otisku certifikátu  
  
1. Otevřete modul snap-in Certifikáty konzoly Microsoft Management Console (MMC). (Viz [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2. V **kořenový adresář konzoly** okno levým podokně klikněte na tlačítko **certifikáty (místní počítač)**.  
  
3. Klikněte na tlačítko **osobní** složky a rozbalte ho.  
  
4. Klikněte na tlačítko **certifikáty** složky a rozbalte ho.  
  
5. V seznamu certifikátů, mějte na paměti **zamýšlené účely** záhlaví. Vyhledejte certifikát, který obsahuje seznam **ověření klienta** jako zamýšlený účel.  
  
6. Dvakrát klikněte na certifikát.  
  
7. V **certifikát** dialogové okno, klikněte na tlačítko **podrobnosti** kartu.  
  
8. Projděte si seznam polí a klikněte na tlačítko **kryptografický otisk**.  
  
9. Kopírování z pole hexadecimálních znaků. Pokud tato miniatura se používá v kódu pro `X509FindType`, odebrat mezery mezi šestnáctkové číslice. Například kryptografický otisk "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" by měl být zadán jako "a909502dd82ae41433e6f83886b00d4277a32a7b" v kódu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>
- [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Postupy: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)
- [Postupy: Vytváření dočasných certifikátů pro použití během vývoje.](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
