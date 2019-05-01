---
title: 'Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 69f79b64250ff46524e7b4720d13351774875a3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61972717"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Postupy: Zobrazení certifikátů pomocí modulu snap-in konzoly MMC
Při vytváření zabezpečeného klienta nebo služby, můžete použít [certifikát](working-with-certificates.md) jako přihlašovací údaje. Například běžný typ přihlašovacích údajů je certifikát X.509, který vytvoříte pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> metody. 

Existují tři různé typy úložišť certifikátů, které můžete zkontrolovat pomocí Microsoft Management Console (MMC) v systémech Windows:

- Místní počítač: Úložiště je místní pro zařízení a globální pro všechny uživatele v zařízení.

- Aktuální uživatel: Úložiště je místní pro aktuální uživatelský účet v zařízení.

- Účet služby: Úložiště je místní pro konkrétní službu na zařízení.

## <a name="view-certificates-in-the-mmc-snap-in"></a>Zobrazit certifikáty modulu snap-in konzoly MMC 

Následující postup ukazuje, jak prozkoumat úložišť na vaše místní zařízení najít odpovídající certifikát: 
  
1. Vyberte **spustit** z **Start** nabídky a pak zadejte *konzoly mmc*. 

    Otevře se konzole MMC. 
  
2. Z **souboru** nabídce vyberte možnost **přidat nebo odebrat modul snap-In**. 
    
    **Přidat nebo odebrat moduly Snap in** zobrazí se okno.
  
3. Z **modul snap in k dispozici** klikněte na položku **certifikáty**a pak vyberte **přidat**.  

    ![Přidat modul snap-in certifikátů](./media/mmc-add-certificate-snap-in.png)
  
4. V **modul snap-in Certifikáty** okně **účet počítače**a pak vyberte **Další**. 
  
    Volitelně můžete vybrat **Můj uživatelský účet** pro aktuálního uživatele nebo **účet služby** pro konkrétní službu. 

    > [!NOTE]
    > Pokud si nejste správce pro vaše zařízení, můžete spravovat certifikáty jenom pro váš uživatelský účet.
  
5. V **vybrat počítač** okně, ponechejte tuto položku **místního počítače** vybrali a pak vyberte **Dokončit**.  
  
6. V **přidat nebo odebrat modul Snap-in** okně **OK**.  
  
    ![Přidat modul snap-in certifikátů](./media/mmc-certificate-snap-in-selected.png)

7. Volitelné: Z **souboru** nabídce vyberte možnost **Uložit** nebo **uložit jako** uložit soubor konzoly MMC pro pozdější použití.  

8. Chcete-li zobrazit vaše certifikáty modulu snap-in konzoly MMC, vyberte **kořenový adresář konzoly** v levém podokně, potom rozbalte **certifikáty (místní počítač)**.

    Zobrazí se seznam adresářů pro každý typ certifikátu. Každý certifikát adresáře můžete zobrazit, export, import a odstranit certifikáty pro jeho.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Zobrazení certifikátů pomocí nástroje Správce certifikátů

Můžete také zobrazit, export, import a odstranit certifikáty pomocí nástroje Správce certifikátů.

### <a name="to-view-certificates-for-the-local-device"></a>Chcete-li zobrazit certifikáty pro místní zařízení

1. Vyberte **spustit** z **Start** nabídky a pak zadejte *certlm.msc*. 

    Zobrazí se nástroj Správce certifikátů pro místní zařízení. 
  
2. Chcete-li zobrazit certifikáty, v části **certifikáty - místní počítač** v levém podokně rozbalte adresář pro typ certifikátu, kterou chcete zobrazit.

### <a name="to-view-certificates-for-the-current-user"></a>Chcete-li zobrazit certifikáty pro aktuálního uživatele

1. Vyberte **spustit** z **Start** nabídky a pak zadejte *certmgr.msc*. 

    Zobrazí se nástroj Certificate Manager pro aktuálního uživatele. 
  
2. Chcete-li zobrazit certifikáty, v části **certifikáty – aktuální uživatel** v levém podokně rozbalte adresář pro typ certifikátu, kterou chcete zobrazit.

## <a name="see-also"></a>Viz také:

- [Práce s certifikáty](working-with-certificates.md)
- [Postupy: Vytváření dočasných certifikátů pro použití během vývoje.](how-to-create-temporary-certificates-for-use-during-development.md)
- [Postupy: Načtení kryptografického otisku certifikátu](how-to-retrieve-the-thumbprint-of-a-certificate.md)
