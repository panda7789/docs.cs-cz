---
title: Pokyny k bráně firewall
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: 2c07d17ebb6bbefa78d12bb128e354112311891a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044953"
---
# <a name="firewall-instructions"></a>Pokyny k bráně firewall
Musíte povolit několik portů nebo programů v bráně firewall, aby mohli ukázky Windows Communication Foundation (WCF) fungovat. Řada ukázek komunikuje pomocí portů v rozsahu 8000-8003 a portu 9000. Brána firewall je ve výchozím nastavení zapnutá a brání přístupu k těmto portům. Pokud chcete bránu firewall povolit pro ukázky, proveďte v závislosti na vašich požadavcích a prostředí zabezpečení jeden z následujících postupů:  
  
- Možnost 1: Interaktivní povolení vzorků při spuštění. Neprovádějte žádné změny konfigurace brány firewall a pokračujte v sestavování a spouštění ukázek. Při spuštění ukázky se zobrazí dialogové okno **Výstraha zabezpečení systému Windows** . Daný vzorový program lze následně přidat interaktivně do odblokovaného seznamu. Pomocí tohoto postupu bude pravděpodobně nutné znovu spustit ukázku.  
  
- Možnost 2: Povolit ukázkové programy předem Spusťte aplet **ovládacího panelu brány Windows Firewall** a povolte ukázkové programy, které chcete spustit. Nejprve musíte vytvořit programy, aby existovaly spustitelné soubory. Podrobnější pokyny najdete v následujícím postupu.  
  
- Možnost 3: Zapněte rozsah portů předem. Spusťte aplet **ovládacího panelu** **brány Windows Firewall** a povolte porty 80, 443, 8000-8003 a 9000, které jsou používány ukázkami. Podrobnější pokyny najdete v následujícím postupu. Tato možnost je méně bezpečná než ostatní, protože umožňuje jakýmkoli programům používat tyto porty, nikoli jenom ukázky.  
  
 Pokud si nejste jistí, který postup chcete použít, vyberte první možnost. Pokud používáte bránu firewall od jiného dodavatele, možná budete muset udělat podobné změny.  
  
> [!IMPORTANT]
> Změna konfigurace brány firewall má vliv na vaše zabezpečení. Doporučujeme, abyste záznamy, které jste provedli, zaznamenali a odebrali je po dokončení práce s ukázkami.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Postup při zapnutí ukázek programů předem  
  
1. Sestavte ukázku.  
  
2. Klikněte na **Start**, klikněte na **Spustit**a `firewall.cpl`zadejte. Tím se otevře aplet **ovládacího panelu brány Windows Firewall** .  
  
    > [!NOTE]
    > Abyste mohli spouštět ukázky, které vyžadují komunikaci přes bránu Windows Firewall, musíte mít oprávnění ke změně nastavení brány firewall. Pokud některá nastavení brány firewall nejsou k dispozici a počítač je připojen k doméně, může správce systému řídit tato nastavení prostřednictvím Zásady skupiny.  
  
3. Provedením jednoho z následujících postupů pro povolení programu v bráně Windows Firewall:  
  
    - V systému Windows 7 nebo Windows Server 2008 R2 klikněte na možnost **Povolení programu nebo funkce přes bránu Windows Firewall**. Klikněte na **změnit nastavení**, připustit **jiný program...** .  
  
    - V [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo[!INCLUDE[lserver](../../../../includes/lserver-md.md)]klikněte na možnost **Zapnout program přes bránu Windows Firewall**.  
  
4. Na kartě **výjimky** klikněte na **Přidat program**.  
  
5. Klikněte na tlačítko **Procházet** a vyberte spustitelný soubor ukázkového plánu, který chcete spustit.  
  
6. Opakujte kroky 4 a 5, dokud nepřidáte spustitelné soubory všech ukázek, které máte v plánu spouštět.  
  
7. Kliknutím na tlačítko **OK** zavřete aplet brány firewall.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Postup při povolení rozsahu portů předem  
  
1. Klikněte na **Start**, klikněte na **Spustit**a `firewall.cpl`zadejte. Tím se otevře aplet **ovládacího panelu brány Windows Firewall** .  
  
2. V systému Windows 7 nebo Windows Server 2008 R2 postupujte podle těchto kroků.  
  
    1. V levém sloupci okna brány Windows Firewall klikněte na **Upřesnit nastavení** .  
  
    2. V levém sloupci klikněte na **příchozí pravidla** .  
  
    3. Klikněte na **Nová pravidla** v pravém sloupci.  
  
    4. Vyberte **port** a klikněte na **Další**.  
  
    5. Vyberte **TCP** a zadejte `8000, 8001, 8002, 8003, 9000, 80, 443` do pole **konkrétní místní porty** .  
  
    6. Klikněte na **Další**.  
  
    7. Vyberte možnost **Povolení připojení**a klikněte na tlačítko **Další** .  
  
    8. Vyberte **doména** a **privátní**a klikněte na **Další**.  
  
    9. Pojmenujte `WCF-WF 4.0 Samples`toto pravidlo a klikněte na **Dokončit**.  
  
    10. Klikněte na **odchozí pravidla** a opakujte kroky c až h.  
  
3. V [!INCLUDE[wv](../../../../includes/wv-md.md)] systému [!INCLUDE[lserver](../../../../includes/lserver-md.md)]nebo použijte následující postup.  
  
    1. Klikněte na možnost **Povolení programu přes bránu Windows Firewall**.  
  
    2. Na kartě **výjimky** klikněte na **Přidat port**.  
  
    3. Zadejte název, jako číslo portu zadejte 8000 a vyberte možnost **TCP** .  
  
    4. Klikněte na tlačítko **změnit obor** , vyberte možnost pouze **Moje síť** (podsíť) a klikněte na tlačítko **OK**.  
  
    5. Opakujte kroky b až d pro porty 8001, 8002, 8003, 9000, 80 a 443.  
  
4. Kliknutím na tlačítko **OK** zavřete aplet brány firewall.  
  
> [!NOTE]
> Po dokončení práce s ukázkami odeberte všechny výjimky brány firewall. Provedete to tak, že otevřete aplet **ovládacího panelu brány Windows Firewall** a odeberete všechny programy nebo položky portů, které byly přidány předchozími postupy.
