---
title: 'Postupy: zobrazení certifikátů pomocí modulu snap-in konzoly MMC'
description: Zabezpečený klient nebo služba WCF může použít certifikát jako přihlašovací údaje. Seznamte se s typy úložišť certifikátů, které můžete prozkoumávat pomocí modulu plug-in konzoly MMC.
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: e63034e48ae836f67f89b454829f7196c94610cd
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246672"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Postupy: zobrazení certifikátů pomocí modulu snap-in konzoly MMC
Když vytváříte zabezpečeného klienta nebo službu, můžete jako přihlašovací údaje použít [certifikát](working-with-certificates.md) . Například běžným typem přihlašovacích údajů je certifikát X. 509, který vytvoříte pomocí <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> metody.

Existují tři různé typy úložišť certifikátů, které můžete prozkoumávat pomocí konzoly MMC (Microsoft Management Console) v systémech Windows:

- Místní počítač: úložiště je místní pro zařízení a globální pro všechny uživatele v zařízení.

- Aktuální uživatel: úložiště je místní k aktuálnímu uživatelskému účtu v zařízení.

- Účet služby: úložiště je místní pro určitou službu na zařízení.

## <a name="view-certificates-in-the-mmc-snap-in"></a>Zobrazení certifikátů v modulu snap-in konzoly MMC

Následující postup ukazuje, jak ověřit obchody na místním zařízení a najít odpovídající certifikát:
  
1. V nabídce **Start** vyberte **Run (spustit** ) a pak zadejte *MMC*.

    Zobrazí se konzola MMC.
  
2. V nabídce **soubor** vyberte **Přidat nebo odebrat modul snap in**.

    Zobrazí se okno **Přidat nebo odebrat moduly snap-in** .
  
3. V seznamu **dostupné moduly snap-in** vyberte **certifikáty**a pak **Přidat**.  

    ![Přidat modul snap-in certifikátů](./media/mmc-add-certificate-snap-in.png)
  
4. V okně **modulu snap-in Certifikáty** vyberte možnost **účet počítače**a potom vyberte možnost **Další**.
  
    Volitelně můžete vybrat možnost **Můj uživatelský účet** pro aktuálního uživatele nebo **účet služby** pro konkrétní službu.

    > [!NOTE]
    > Pokud nejste správcem vašeho zařízení, můžete spravovat certifikáty jenom pro svůj uživatelský účet.
  
5. V okně **Vybrat počítač** ponechte vybraný **místní počítač** a pak vyberte **Dokončit**.  
  
6. V okně **Přidat nebo odebrat modul snap-in** vyberte **OK**.  
  
    ![Přidat modul snap-in certifikátů](./media/mmc-certificate-snap-in-selected.png)

7. Volitelné: v nabídce **soubor** vyberte **Uložit** nebo **Uložit jako** a uložte soubor konzoly MMC pro pozdější použití.  

8. Chcete-li zobrazit certifikáty v modulu snap-in konzoly MMC, vyberte v levém podokně **kořenový adresář konzoly** a potom rozbalte položku **certifikáty (místní počítač)**.

    Zobrazí se seznam adresářů pro každý typ certifikátu. Z každého adresáře certifikátu můžete zobrazit, exportovat, importovat a odstranit jeho certifikáty.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Zobrazení certifikátů pomocí nástroje Správce certifikátů

Pomocí nástroje Správce certifikátů můžete také zobrazit, exportovat, importovat a odstranit certifikáty.

### <a name="to-view-certificates-for-the-local-device"></a>Zobrazení certifikátů pro místní zařízení

1. V nabídce **Start** vyberte **Run (spustit** ) a pak zadejte *Certlm. msc*.

    Zobrazí se nástroj Správce certifikátů pro místní zařízení.
  
2. Certifikáty zobrazíte tak, že v části **certifikáty – místní počítač** v levém podokně rozbalíte adresář pro typ certifikátu, který chcete zobrazit.

### <a name="to-view-certificates-for-the-current-user"></a>Zobrazení certifikátů pro aktuálního uživatele

1. V nabídce **Start** vyberte **Run (spustit** ) a pak zadejte *certmgr. msc*.

    Zobrazí se nástroj Správce certifikátů pro aktuálního uživatele.
  
2. Chcete-li zobrazit certifikáty, v části **Certifikáty – aktuální uživatel** v levém podokně rozbalte adresář pro typ certifikátu, který chcete zobrazit.

## <a name="see-also"></a>Viz také

- [Práce s certifikáty](working-with-certificates.md)
- [Postupy: vytváření dočasných certifikátů pro použití během vývoje](how-to-create-temporary-certificates-for-use-during-development.md)
- [Postupy: Načtení kryptografického otisku certifikátu](how-to-retrieve-the-thumbprint-of-a-certificate.md)
