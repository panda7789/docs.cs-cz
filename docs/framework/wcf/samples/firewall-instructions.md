---
title: Pokyny k bráně firewall
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: f1b576b4e413fa3bae70ef1eb8f8ed768e28e309
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051933"
---
# <a name="firewall-instructions"></a>Pokyny k bráně firewall
Je nutné povolit několik portů a programů v bráně firewall tak, aby ukázky Windows Communication Foundation (WCF), můžou fungovat. Mnoho vzorků komunikaci prostřednictvím portů v rozsahu 8000-8003 a portu 9000. Brána firewall je ve výchozím nastavení zapnutá a brání v přístupu k těmto portům. Pokud chcete povolit bránu firewall pro ukázky, proveďte jednu z následujících postupů, v závislosti na vašich požadavcích a zabezpečení prostředí:  
  
- Option 1: Povolte interaktivní ukázky při spuštění. Neprovádějte žádné změny zálohy konfigurace brány firewall a pokračujte začít sestavovat a spouštět ukázky. Při spuštění ukázky **výstraha zabezpečení Windows** zobrazí se dialogové okno. Ukázkový program dotyčný je potom možné přidat interaktivně odblokované seznamu. V tomto návodu budete muset znovu spusťte ukázku.  
  
- Option 2: Povolte ukázkové programy předem. Spustit **ovládacích panelů Windows Firewall** aplet a povolte ukázka programy plánu pro spuštění. Programy musí nejprve sestavení, spustitelné soubory existují. Podrobné pokyny najdete v následujícím postupu.  
  
- Možnost 3: Povolte rozsah portů předem. Spustit **brány Windows Firewall** **ovládací panely** aplet a povolte porty 80, 443, 8000 8003 a 9000, které se používají ve vzorcích. Podrobné pokyny najdete v následujícím postupu. Tato možnost je méně bezpečné než ostatní, protože umožňuje libovolné aplikaci pro používání těchto portů, nejen ukázky.  
  
 Pokud si nejste jisti, který postup máte použít, zvolte první možnost. Pokud používáte firewall od jiného dodavatele, může být nutné provést změny podobné změny.  
  
> [!IMPORTANT]
>  Když změníte konfiguraci brány firewall má vliv na zabezpečení. Doporučujeme záznamu změny Ujistěte se a odstranit je při dokončení práce s ukázkami.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Chcete-li povolit ukázkové programy předem  
  
1. Sestavte ukázku.  
  
2. Klikněte na tlačítko **Start**, klikněte na tlačítko **spustit**a typ `firewall.cpl`. Tím se otevře **ovládacích panelů Windows Firewall** aplet.  
  
    > [!NOTE]
    >  Musíte mít oprávnění ke změně nastavení brány Firewall pro spuštění ukázky, které potřebují komunikovat přes bránu Windows Firewall. Pokud některé nastavení brány firewall nejsou k dispozici a je počítač připojen k doméně, může správce systému řízení těchto nastavení prostřednictvím zásad skupiny.  
  
3. Proveďte jeden z následujících provozních konkrétní kroky pro povolit programu přes bránu Windows Firewall:  
  
    - Na Windows 7 nebo Windows Server 2008 r2, klikněte na tlačítko **povolit program nebo funkci průchod bránou Windows Firewall**. Klikněte na tlačítko **změnit nastavení**, povolit **jiný Program...** .  
  
    - Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], klikněte na tlačítko **programu přes bránu Windows Firewall povolit**.  
  
4. Na **výjimky** klikněte na tlačítko **přidat Program**.  
  
5. Klikněte na tlačítko **Procházet** tlačítko a vyberte spustitelný soubor, ukázky, které plánujete spouštět.  
  
6. Opakujte kroky 4 a 5, dokud nepřidáte spustitelné soubory všechny ukázky, které chcete spustit.  
  
7. Klikněte na tlačítko **OK** zavřete aplet brány firewall.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Povolit rozsah portů předem  
  
1. Klikněte na tlačítko **Start**, klikněte na tlačítko **spustit**a typ `firewall.cpl`. Tím se otevře **ovládacích panelů Windows Firewall** aplet.  
  
2. Na Windows 7 nebo Windows Server 2008 R2 postupujte podle těchto kroků.  
  
    1. Klikněte na tlačítko **upřesňující nastavení** v levém sloupci okna brána Windows Firewall.  
  
    2. Klikněte na tlačítko **příchozí pravidla** v levém sloupci.  
  
    3. Klikněte na tlačítko **nová pravidla** v pravém sloupci.  
  
    4. Vyberte **Port** a klikněte na tlačítko **Další**.  
  
    5. Vyberte **TCP** a zadejte `8000, 8001, 8002, 8003, 9000, 80, 443` v **určité místní porty** pole.  
  
    6. Klikněte na **Další**.  
  
    7. Vyberte **povolit připojení**a klikněte na tlačítko **Další** .  
  
    8. Vyberte **domény** a **privátní**a klikněte na tlačítko **Další**.  
  
    9. Název tohoto pravidla `WCF-WF 4.0 Samples`a klikněte na tlačítko **Dokončit**.  
  
    10. Klikněte na tlačítko **odchozí pravidla** a opakujte kroky c h.  
  
3. Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], postupujte podle těchto kroků.  
  
    1. Klikněte na tlačítko **programu přes bránu Windows Firewall povolit**.  
  
    2. Na **výjimky** klikněte na tlačítko **přidat Port**.  
  
    3. Zadejte název, zadejte jako číslo portu 8000 a vyberte **TCP** možnost.  
  
    4. Klikněte na tlačítko **změnit obor** tlačítka, vyberte **Moje sítě** jedinou možností (podsítě) a klikněte na tlačítko **OK**.  
  
    5. Opakujte kroky b až d pro porty 8001, 8002 8003, 9000, 80 a 443.  
  
4. Klikněte na tlačítko **OK** zavřete aplet brány firewall.  
  
> [!NOTE]
>  Po dokončení práce s ukázkami, odeberte všechny výjimky brány firewall. Chcete-li to provést, otevřete **ovládacích panelů Windows Firewall** aplet a odebrání všech programů nebo port položky, které byly přidány podle předchozích kroků.
