---
title: "Pokyny k bráně firewall"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0aac3a161b0482bad1a32f5223d2031402a632cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="firewall-instructions"></a>Pokyny k bráně firewall
Musíte povolit několik portů nebo programů v bráně firewall tak, která [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ukázky, můžou fungovat. Řadu ukázky komunikovat prostřednictvím portů v rozsahu 8000-8003 a portu 9000. Brána firewall je ve výchozím nastavení zapnuta a brání přístupu k těmto portům. Pokud chcete povolit bránu firewall pro ukázky, proveďte jednu z následujících postupů, v závislosti na vašich požadavcích a zabezpečení prostředí:  
  
-   Možnost 1: Povolení interaktivní ukázky během spuštění. Neprovedete žádné změny záloh konfigurace brány firewall a pokračujte začít sestavovat a spouštět ukázky. Když se spustí ukázku, **výstraha zabezpečení Windows** zobrazí se dialogové okno. Ukázkový program dotyčném lze přidat interaktivně odblokuje seznamu. Pomocí tohoto postupu budete muset znovu spusťte vzorku.  
  
-   Možnost 2: Povolení předem ukázkové aplikace. Spuštění **ovládacích panelů Windows Firewall** aplet a povolit ukázku programy plán ke spuštění. Programy musí nejprve vytvořit tak spustitelné soubory existují. Podrobnější pokyny najdete v následujícím postupu.  
  
-   Možnost 3: Povolení předem rozsah portů. Spuštění **brány Windows Firewall** **ovládací panely** aplet a povolit porty 80 a 443, 8000 8003 a 9000, které jsou používány ukázky. Podrobnější pokyny najdete v následujícím postupu. Tato možnost je méně bezpečné než jiné, protože umožňuje žádné program použít tyto porty, ne jenom ukázky.  
  
 Pokud si nejste jistí, z kterého postupu se má použít, zvolte první možnost. Pokud používáte firewall od jiného dodavatele, musíte může provádět podobné změny.  
  
> [!IMPORTANT]
>  Změna konfigurace brány firewall má vliv na zabezpečení. Doporučuje se záznamu změny, ujistěte se a po skončení práce s ukázky je odebrat.  
  
### <a name="to-enable-samples-programs-in-advance"></a>Chcete-li povolit programy ukázky předem  
  
1.  Sestavte ukázku.  
  
2.  Klikněte na tlačítko **spustit**, klikněte na tlačítko **spustit**a typ `firewall.cpl`. Tím se otevře **ovládacích panelů Windows Firewall** aplet.  
  
    > [!NOTE]
    >  Musíte mít oprávnění ke změně nastavení brány Firewall ke spuštění ukázky, které potřebují ke komunikaci přes bránu Windows Firewall. Pokud některá nastavení brány firewall nejsou k dispozici a je počítač připojen k doméně, správce systému může být tato nastavení řídí prostřednictvím zásad skupiny.  
  
3.  Proveďte jeden z následujících operační konkrétní kroků povolit program přes bránu Windows Firewall:  
  
    -   V systému Windows 7 nebo Windows Server 2008 r2, klikněte na tlačítko **povolit program nebo funkci průchod bránou Windows Firewall**. Klikněte na tlačítko **změnit nastavení**, povolit **jiný Program...** .  
  
    -   Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], klikněte na tlačítko **programu přes bránu Windows Firewall povolit**.  
  
4.  Na **výjimky** , klikněte na **přidat Program**.  
  
5.  Klikněte **Procházet** tlačítko a vyberte spustitelný soubor, ukázky, které chcete spustit.  
  
6.  Opakujte kroky 4 a 5, dokud nepřidáte všechny ukázky, které plánujete spouštět spustitelné soubory.  
  
7.  Klikněte na tlačítko **OK** zavřete apletu brány firewall.  
  
### <a name="to-enable-a-port-range-in-advance"></a>Chcete-li povolit rozsah portů předem  
  
1.  Klikněte na tlačítko **spustit**, klikněte na tlačítko **spustit**a typ `firewall.cpl`. Tím se otevře **ovládacích panelů Windows Firewall** aplet.  
  
2.  Windows 7 nebo Windows Server 2008 R2 postupujte podle těchto kroků.  
  
    1.  Klikněte na tlačítko **upřesňující nastavení** v levém sloupci okna brány Windows Firewall.  
  
    2.  Klikněte na tlačítko **příchozí pravidla** v levém sloupci.  
  
    3.  Klikněte na tlačítko **nové pravidel** v pravém sloupci.  
  
    4.  Vyberte **Port** a klikněte na tlačítko **Další**.  
  
    5.  Vyberte **TCP** a zadejte `8000, 8001, 8002, 8003, 9000, 80, 443` v **určité místní porty** pole.  
  
    6.  Klikněte na tlačítko **Další**.  
  
    7.  Vyberte **povolit připojení**a klikněte na tlačítko **Další** .  
  
    8.  Vyberte **domény** a **privátní**a klikněte na tlačítko **Další**.  
  
    9. Název tohoto pravidla `WCF-WF 4.0 Samples`a klikněte na tlačítko **Dokončit**.  
  
    10. Klikněte na tlačítko **odchozí pravidla** a opakujte kroky c h.  
  
3.  Na [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo [!INCLUDE[lserver](../../../../includes/lserver-md.md)], postupujte podle těchto kroků.  
  
    1.  Klikněte na tlačítko **programu přes bránu Windows Firewall povolit**.  
  
    2.  Na **výjimky** , klikněte na **přidat Port**.  
  
    3.  Zadejte název a 8000 jako číslo portu a vyberte **TCP** možnost.  
  
    4.  Klikněte na tlačítko **změnit obor** tlačítko, vyberte **Moje sítě** pouze možnost (podsítě) a klikněte na tlačítko **OK**.  
  
    5.  Opakujte kroky b d pro porty 8001, 8002, 8003, 9000, 80 a 443.  
  
4.  Klikněte na tlačítko **OK** zavřete apletu brány firewall.  
  
> [!NOTE]
>  Po dokončení práce s ukázky, odeberte všechny výjimky brány firewall. Chcete-li to provést, otevřete **ovládacích panelů Windows Firewall** aplet a odeberte všechny programy nebo portu položky, které byly přidány jako předchozí postupy.
