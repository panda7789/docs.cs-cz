---
title: 'Postupy: načtení kryptografického otisku certifikátu'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: d827c2c5f407c3041a31efbc06fcfed205bef458
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33492431"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Postupy: načtení kryptografického otisku certifikátu
Při psaní aplikace Windows Communication Foundation (WCF), která používá certifikátu X.509. certifikát pro ověřování, je často nutné zadat najdou deklarace v certifikátu. Například musíte zadat deklaraci identity kryptografický otisk při použití <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> výčet ve <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda. Hledání hodnota deklarace identity vyžaduje dva kroky. První otevřete modul snap-in Certifikáty konzoly Microsoft Management Console (MMC). (Viz [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Druhý podle postupu popsaného tady, vyhledejte příslušný certifikát a zkopírujte jeho kryptografický otisk (nebo jiné hodnoty deklarace identity).  
  
 Pokud používáte certifikát pro ověřování služby, je důležité si uvědomit, hodnota **vystaveno pro** sloupce (první sloupec v konzole). Při použití Secure Sockets Layer (SSL), jako je zabezpečení přenosu, jedním z první kontroly provést k porovnání základní adresa identifikátoru URI (Uniform Resource) služby **vystaveno pro** hodnotu. Hodnoty musí odpovídat nebo se zastavit proces ověřování.  
  
 Můžete také použít nástroj Makecert.exe z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] SDK k vytvoření dočasného certifikátů pro použití pouze během vývoje. Ve výchozím nastavení ale tento certifikát není vystavený certifikační autoritou a nelze jej použít pro produkční účely. Další informace najdete v tématu [postupy: vytvoření dočasné certifikáty pro použití při vývoji](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Načíst kryptografický otisk certifikátu  
  
1.  Otevřete modul snap-in Certifikáty konzoly Microsoft Management Console (MMC). (Viz [postupy: zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2.  V **kořenový adresář konzoly** okno je levé podokno, klikněte na tlačítko **certifikáty (místní počítač)**.  
  
3.  Klikněte **osobní** rozbalte složku.  
  
4.  Klikněte **certifikáty** rozbalte složku.  
  
5.  V seznamu certifikátů, pamatujte **určený pro účely** záhlaví. Najít certifikát, který obsahuje seznam **ověření klienta** jako zamýšlený účel.  
  
6.  Dvakrát klikněte na certifikát.  
  
7.  V **certifikát** dialogové okno, klikněte na tlačítko **podrobnosti** kartě.  
  
8.  Vyhledejte v seznamu polí a klikněte na tlačítko **kryptografický otisk**.  
  
9. Zkopírujte hexadecimálních znaků z pole. Pokud se tímto kryptografickým otiskem používá v kódu `X509FindType`, odebrat mezery mezi hexadecimální číslice. Například kryptografický otisk "a9 09 50 2d d8 2a e4 14 33 e6 f8 38 86 b0 0d 42 77 a3 2a 7b" musí být zadány ve tvaru "a909502dd82ae41433e6f83886b00d4277a32a7b" v kódu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [Postupy: Konfigurace portu s certifikátem SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Postupy: Vytváření dočasných certifikátů pro použití během vývoje](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
