---
title: 'Postup: Zobrazení certifikátů pomocí modulu snap-in Konzoly MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184787"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Postup: Zobrazení certifikátů pomocí modulu snap-in Konzoly MMC
Při vytváření zabezpečeného klienta nebo služby můžete jako pověření použít [certifikát.](working-with-certificates.md) Běžným typem pověření je například certifikát X.509, <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> který vytvoříte pomocí metody.

Existují tři různé typy úložišť certifikátů, které můžete prozkoumat pomocí konzoly MMC (MMC) v systémech Windows:

- Místní počítač: Úložiště je místní pro zařízení a globální pro všechny uživatele v zařízení.

- Aktuální uživatel: Úložiště je místní aktuální uživatelský účet v zařízení.

- Účet služby: Úložiště je místní pro konkrétní službu v zařízení.

## <a name="view-certificates-in-the-mmc-snap-in"></a>Zobrazení certifikátů v modulu snap-in konzoly MMC

Následující postup ukazuje, jak zkontrolovat obchody v místním zařízení najít odpovídající certifikát:
  
1. Z nabídky **Start** vyberte **Spustit** a zadejte *konzolu MMC*.

    Zobrazí se konzola MMC.
  
2. V nabídce **Soubor** vyberte **Přidat nebo odebrat přichycení**.

    Zobrazí se okno **Přidat nebo odebrat moduly snap-in.**
  
3. V seznamu **Dostupné moduly snap-in** zvolte **Certifikáty**a pak vyberte **Přidat**.  

    ![Přidání modulu snap-in certifikátu](./media/mmc-add-certificate-snap-in.png)
  
4. V okně **modulu snap-in Certifikáty** vyberte **Účet počítače**a pak vyberte **Další**.
  
    Volitelně můžete vybrat **můj uživatelský účet** pro aktuální uživatelský účet nebo účet **služby** pro konkrétní službu.

    > [!NOTE]
    > Pokud nejste správcem zařízení, můžete spravovat certifikáty pouze pro svůj uživatelský účet.
  
5. V okně **Vybrat počítač** ponechejte vybrat **místní počítač** a pak vyberte **Dokončit**.  
  
6. V okně **Přidat nebo odebrat modul snap-in** vyberte **OK**.  
  
    ![Přidání modulu snap-in certifikátu](./media/mmc-certificate-snap-in-selected.png)

7. Volitelné: V nabídce **Soubor** vyberte **Uložit** nebo **Uložit jako,** chcete-li soubor konzoly MMC uložit pro pozdější použití.  

8. Chcete-li zobrazit certifikáty v modulu snap-in konzoly MMC, vyberte v levém podokně **položku Kořenová konzola** a potom rozbalte **položku Certifikáty (místní počítač).**

    Zobrazí se seznam adresářů pro každý typ certifikátu. V každém adresáři certifikátů můžete jeho certifikáty zobrazit, exportovat, importovat a odstranit.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Zobrazení certifikátů pomocí nástroje Správce certifikátů

Certifikáty můžete také zobrazit, exportovat, importovat a odstraňovat pomocí nástroje Správce certifikátů.

### <a name="to-view-certificates-for-the-local-device"></a>Zobrazení certifikátů pro místní zařízení

1. Z nabídky **Start** vyberte **Spustit** a zadejte *certlm.msc*.

    Zobrazí se nástroj Správce certifikátů pro místní zařízení.
  
2. Chcete-li zobrazit certifikáty, rozbalte v levém podokně v části **Certifikáty – místní počítač** adresář pro typ certifikátu, který chcete zobrazit.

### <a name="to-view-certificates-for-the-current-user"></a>Zobrazení certifikátů pro aktuálního uživatele

1. Z nabídky **Start** vyberte **Spustit** a zadejte *certmgr.msc*.

    Zobrazí se nástroj Správce certifikátů pro aktuálního uživatele.
  
2. Chcete-li zobrazit certifikáty, rozbalte v části **Certifikáty - Aktuální uživatel** v levém podokně adresář pro typ certifikátu, který chcete zobrazit.

## <a name="see-also"></a>Viz také

- [Práce s certifikáty](working-with-certificates.md)
- [Postup: Vytvoření dočasných certifikátů pro použití během vývoje](how-to-create-temporary-certificates-for-use-during-development.md)
- [Postup: Načtení kryptografického otisku certifikátu](how-to-retrieve-the-thumbprint-of-a-certificate.md)
