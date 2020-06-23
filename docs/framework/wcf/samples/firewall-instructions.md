---
title: Pokyny k bráně firewall
description: Přečtěte si, jak povolit porty nebo programy v bráně firewall pro ukázky WCF. V závislosti na vašich požadavcích a prostředí zabezpečení použijte jeden z těchto postupů.
ms.date: 03/30/2017
ms.assetid: a7dc429f-65ac-4faf-974a-77d5fb977fe1
ms.openlocfilehash: de55d067960b8f2096c129f6feaf037219e06a96
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246138"
---
# <a name="firewall-instructions"></a>Pokyny pro bránu firewall

Musíte povolit několik portů nebo programů v bráně firewall, aby mohli ukázky Windows Communication Foundation (WCF) fungovat. Řada ukázek komunikuje pomocí portů v rozsahu 8000-8003 a portu 9000. Brána firewall je ve výchozím nastavení zapnutá a brání přístupu k těmto portům. Pokud chcete bránu firewall povolit pro ukázky, proveďte v závislosti na vašich požadavcích a prostředí zabezpečení jeden z následujících postupů:

- Možnost 1: interaktivní povolení vzorků při spuštění. Neprovádějte žádné změny konfigurace brány firewall a pokračujte v sestavování a spouštění ukázek. Při spuštění ukázky se zobrazí dialogové okno **Výstraha zabezpečení systému Windows** . Daný vzorový program lze následně přidat interaktivně do odblokovaného seznamu. Pomocí tohoto postupu bude pravděpodobně nutné znovu spustit ukázku.

- Možnost 2: povolení předem ukázkových programů. Spusťte aplet **ovládacího panelu brány Windows Firewall** a povolte ukázkové programy, které chcete spustit. Nejprve musíte vytvořit programy, aby existovaly spustitelné soubory. Podrobnější pokyny najdete v následujícím postupu.

- Možnost 3: Zapněte si rozsah portů předem. Spusťte aplet **ovládacího panelu brány Windows Firewall** a povolte porty 80, 443, 8000-8003 a 9000, které jsou používány ukázkami. Podrobnější pokyny najdete v následujícím postupu. Tato možnost je méně bezpečná než ostatní, protože umožňuje jakýmkoli programům používat tyto porty, nikoli jenom ukázky.

Pokud si nejste jistí, který postup chcete použít, vyberte první možnost. Pokud používáte bránu firewall od jiného dodavatele, možná budete muset udělat podobné změny.

> [!IMPORTANT]
> Změna konfigurace brány firewall má vliv na vaše zabezpečení. Doporučujeme, abyste záznamy, které jste provedli, zaznamenali a odebrali je po dokončení práce s ukázkami.

## <a name="enable-samples-programs-in-advance"></a>Povolit ukázkové programy předem

1. Sestavte ukázku.

2. Vyberte **Spustit**  >  **běh**a zadejte `firewall.cpl` . Tím se otevře aplet **ovládacího panelu brány Windows Firewall** .

    > [!NOTE]
    > Abyste mohli spouštět ukázky, které vyžadují komunikaci přes bránu Windows Firewall, musíte mít oprávnění ke změně nastavení brány firewall. Pokud některá nastavení brány firewall nejsou k dispozici a počítač je připojen k doméně, může správce systému řídit tato nastavení prostřednictvím Zásady skupiny.

3. Proveďte jeden z následujících kroků pro konkrétní operační systém, aby bylo možné program přes bránu Windows Firewall:

    - V systému Windows 7 nebo Windows Server 2008 R2 klikněte na možnost **Povolení programu nebo funkce přes bránu Windows Firewall**. Klikněte na **změnit nastavení**  >  .**umožní vám jiný program**.

    - V systému Windows Vista nebo Windows Server 2008 klikněte na možnost **Povolení programu přes bránu Windows Firewall**.

4. Na kartě **výjimky** klikněte na **Přidat program**.

5. Klikněte na tlačítko **Procházet** a vyberte spustitelný soubor ukázkového plánu, který chcete spustit.

6. Opakujte kroky 4 a 5, dokud nepřidáte spustitelné soubory všech ukázek, které máte v plánu spouštět.

7. Kliknutím na tlačítko **OK** zavřete aplet brány firewall.

## <a name="enable-a-port-range-in-advance"></a>Povolit rozsah portů předem

1. Vyberte **Spustit**  >  **běh**a zadejte `firewall.cpl` . Tím se otevře aplet **ovládacího panelu brány Windows Firewall** .

2. V systému Windows 7 nebo Windows Server 2008 R2 postupujte podle těchto kroků.

    1. V levém sloupci okna brány Windows Firewall klikněte na **Upřesnit nastavení** .

    2. V levém sloupci klikněte na **příchozí pravidla** .

    3. Klikněte na **Nová pravidla** v pravém sloupci.

    4. Vyberte **port** a klikněte na **Další**.

    5. Vyberte **TCP** a zadejte `8000, 8001, 8002, 8003, 9000, 80, 443` do pole **konkrétní místní porty** .

    6. Klikněte na **Další**.

    7. Vyberte možnost **Povolení připojení**a klikněte na tlačítko **Další** .

    8. Vyberte **doména** a **privátní**a klikněte na **Další**.

    9. Pojmenujte toto pravidlo `WCF-WF 4.0 Samples` a klikněte na **Dokončit**.

    10. Klikněte na **odchozí pravidla** a opakujte kroky c až h.

3. V systému Windows Vista nebo Windows Server 2008 postupujte podle těchto kroků.

    1. Klikněte na možnost **Povolení programu přes bránu Windows Firewall**.

    2. Na kartě **výjimky** klikněte na **Přidat port**.

    3. Zadejte název, jako číslo portu zadejte 8000 a vyberte možnost **TCP** .

    4. Klikněte na tlačítko **změnit obor** , vyberte možnost pouze **Moje síť** (podsíť) a klikněte na tlačítko **OK**.

    5. Opakujte kroky b až d pro porty 8001, 8002, 8003, 9000, 80 a 443.

4. Kliknutím na tlačítko **OK** zavřete aplet brány firewall.

> [!NOTE]
> Po dokončení práce s ukázkami odeberte všechny výjimky brány firewall. Provedete to tak, že otevřete aplet **ovládacího panelu brány Windows Firewall** a odeberete všechny programy nebo položky portů, které byly přidány předchozími postupy.
