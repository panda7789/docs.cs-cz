---
title: 'Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC'
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: d924121b9d9fa267fa7d1ada13c9dc5f5bf1523d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493347"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC
Běžný typ přihlašovacích údajů je certifikát X.509. Při vytváření zabezpečené služby nebo klientů, můžete zadat, certifikát se dá použít jako pověření klienta služby nebo pomocí metody, jako <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> metoda. Metoda vyžaduje různé parametry, jako je například úložiště, kde je uložen certifikát a hodnotu mají použít při hledání pro certifikát. Následující postup předvádí, jak prozkoumat úložiště na počítače, který chcete najít příslušný certifikát. Příklad hledání kryptografický otisk certifikátu, naleznete v části [postupy: načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>K zobrazení certifikátů modulu snap-in konzoly MMC  
  
1.  Otevřete okno příkazového řádku.  
  
2.  Typ `mmc` a stiskněte klávesu ENTER. Všimněte si, že chcete-li zobrazit certifikáty v úložišti místního počítače, musí být v roli správce.  
  
3.  Na **soubor** nabídky, klikněte na tlačítko **přidat nebo odebrat modul snap-In**.  
  
4.  Klikněte na tlačítko **přidat**.  
  
5.  V **přidat samostatný modul Snap-in** dialogové okno, vyberte **certifikáty**.  
  
6.  Klikněte na tlačítko **přidat**.  
  
7.  V **modul snap-in Certifikáty** dialogové okno, vyberte **účet počítače** a klikněte na tlačítko **Další**. Volitelně můžete vybrat **Moje uživatelský účet** nebo **účet služby**. Pokud si nejste správcem počítače, můžete spravovat certifikáty jenom pro váš uživatelský účet.  
  
8.  V **vybrat počítač** dialogové okno, klikněte na tlačítko **Dokončit**.  
  
9. V **přidat samostatný modul Snap-in** dialogové okno, klikněte na tlačítko **Zavřít**.  
  
10. Na **přidat nebo odebrat modul Snap-in** dialogové okno, klikněte na tlačítko **OK**.  
  
11. V **kořenový adresář konzoly** okně klikněte na tlačítko **certifikáty (místní počítač)** zobrazíte certifikát uloží pro počítač.  
  
12. Volitelné. Chcete-li zobrazit certifikáty pro váš účet, opakujte kroky 3 až 6. V kroku 7, místo výběru **účet počítače**, klikněte na tlačítko **Moje uživatelský účet** a opakujte kroky 8 až 10.  
  
13. Volitelné. Na **soubor** nabídky, klikněte na tlačítko **Uložit** nebo **uložit jako**. Uložte soubor konzoly pro pozdější použití.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Zobrazení certifikátů pomocí Internet Exploreru  
 Můžete také zobrazit, exportovat, importovat a odstranění certifikátů v aplikaci Internet Explorer.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>K zobrazení certifikátů pomocí Internet Exploreru  
  
1.  V aplikaci Internet Explorer, klikněte na tlačítko **nástroje**, pak klikněte na tlačítko **Možnosti Internetu** zobrazíte **Možnosti Internetu** dialogové okno.  
  
2.  Klikněte **obsahu** kartě.  
  
3.  V části **certifikáty**, klikněte na tlačítko **certifikáty**.  
  
4.  Chcete-li zobrazit podrobnosti o libovolný certifikát, vyberte certifikát a klikněte na tlačítko **zobrazení**.  
  
## <a name="see-also"></a>Viz také  
 [Práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Postupy: Vytváření dočasných certifikátů pro použití během vývoje](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [Postupy: Načtení kryptografického otisku certifikátu](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
