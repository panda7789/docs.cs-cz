---
title: 'Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 72fd6a1be2f33e1bfeb08fd43f3436627ee842e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521579"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC
Společný typ přihlašovacích údajů je certifikát X.509. Při vytváření zabezpečených služeb a klientů, můžete určit certifikát použít jako pověření klienta nebo služby pomocí metody, jako <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metody. Metoda vyžaduje různé parametry, jako jsou úložiště, kde je certifikát uložený a hodnoty pro použití při hledání certifikátu. Následující postup ukazuje, jak prozkoumat úložišti v počítači se najít odpovídající certifikát. Příklad toho, jak najít kryptografický otisk certifikátu, naleznete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>Chcete-li zobrazit certifikáty modulu snap-in konzoly MMC  
  
1.  Otevřete okno příkazového řádku.  
  
2.  Typ `mmc` a stiskněte klávesu ENTER. Všimněte si, že chcete zobrazit certifikáty v úložišti místního počítače, musí být v roli správce.  
  
3.  Na **souboru** nabídky, klikněte na tlačítko **přidat nebo odebrat modul snap-In**.  
  
4.  Klikněte na **Přidat**.  
  
5.  V **přidat samostatný modul Snap-in** dialogu **certifikáty**.  
  
6.  Klikněte na **Přidat**.  
  
7.  V **modul snap-in Certifikáty** dialogu **účet počítače** a klikněte na tlačítko **Další**. Volitelně můžete vybrat **tento uživatelský účet** nebo **účet služby**. Pokud nejste správcem tohoto počítače, můžete spravovat certifikáty jenom pro váš uživatelský účet.  
  
8.  V **vybrat počítač** dialogové okno, klikněte na tlačítko **Dokončit**.  
  
9. V **přidat samostatný modul Snap-in** dialogové okno, klikněte na tlačítko **Zavřít**.  
  
10. Na **Přidat/odebrat modul Snap-in** dialogové okno, klikněte na tlačítko **OK**.  
  
11. V **kořenový adresář konzoly** okna, klikněte na tlačítko **certifikáty (místní počítač)** zobrazíte certifikát uloží pro počítač.  
  
12. Volitelné. Pokud chcete zobrazit certifikáty pro váš účet, opakujte kroky 3 až 6. V kroku 7, místo výběru **účet počítače**, klikněte na tlačítko **tento uživatelský účet** a opakujte kroky 8 až 10.  
  
13. Volitelné. Na **souboru** nabídky, klikněte na tlačítko **Uložit** nebo **uložit jako**. Uložte soubor konzoly pro pozdější použití.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Zobrazení certifikátů pomocí Internet Exploreru  
 Můžete také zobrazit, export, import a odstranit certifikáty pomocí aplikace Internet Explorer.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>K zobrazení certifikátů pomocí Internet Exploreru  
  
1.  V aplikaci Internet Explorer, klikněte na tlačítko **nástroje**, pak klikněte na tlačítko **Možnosti Internetu** zobrazíte **Možnosti Internetu** dialogové okno.  
  
2.  Klikněte na tlačítko **obsahu** kartu.  
  
3.  V části **certifikáty**, klikněte na tlačítko **certifikáty**.  
  
4.  Chcete-li zobrazit podrobnosti o některý z certifikátů, vyberte certifikát a klikněte na tlačítko **zobrazení**.  
  
## <a name="see-also"></a>Viz také:
- [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Postupy: Vytváření dočasných certifikátů pro použití během vývoje.](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
- [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
