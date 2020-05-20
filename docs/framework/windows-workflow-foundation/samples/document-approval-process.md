---
title: Proces schválení dokumentu
description: Tato ukázka předvádí mnoho funkcí programovací model Windows Workflow Foundation a Windows Communication Foundation ve scénáři procesu schválení dokumentu.
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: 18b4f978e9234daf22395f0d2f6f0889d0edf966
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421407"
---
# <a name="document-approval-process"></a>Proces schválení dokumentu

Tato ukázka předvádí použití mnoha funkcí programovací model Windows Workflow Foundation (WF) a Windows Communication Foundation (WCF) společně. Společně implementují scénář procesu schvalování dokumentů. Klientská aplikace může odesílat dokumenty ke schválení a schvalování dokumentů. K dispozici je aplikace Správce schválení, která usnadňuje komunikaci mezi klienty a vynucuje pravidla schvalovacího procesu. Proces schvalování je pracovní postup, který může provést několik typů schválení. Aktivity existují pro získání jediného schválení, schválení kvora (procento sady schvalovatelů) a složitý proces schvalování, který se skládá z kvora a jednoho schválení v rámci sekvence.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`

## <a name="sample-details"></a>Podrobnosti ukázky

Následující obrázek znázorňuje pracovní postup procesu schvalování dokumentů:

![Pracovní postup procesu schválení dokumentu](./media/document-approval-process/document-approval-process.jpg)

V perspektivě klienta funkce procesu schvalování funguje takto:

1. Klient se přihlásí jako uživatel v systému schvalovacích procesů.

2. Klient WCF odesílá do služby WCF hostované aplikací Správce schvalování.

3. Klientovi se vrátí jedinečné ID uživatele. Klient se teď může zúčastnit procesů schvalování.

4. Po připojení může klient odeslat dokument ke schválení pomocí jednoho, kvora nebo složitých procesů schvalování.

5. Klikne na tlačítko v rozhraní klienta a spustí se instance pracovního postupu na hostiteli služby pracovního postupu klienta.

6. Pracovní postup odešle žádost o schválení aplikaci Správce schvalování.

7. Správce pracovních postupů spustí pracovní postup na vlastní straně, který bude reprezentovat schvalovací proces.

8. Po spuštění pracovního postupu schválení správce se výsledky odešlou zpátky klientovi.

9. Klient zobrazí výsledky.

10. Klient může obdržet žádost o schválení a odpovědět na žádost v jakémkoli okamžiku.

11. Služba WCF hostovaná v klientovi může obdržet žádost o schválení z aplikace Správce schvalování.

12. Informace o dokumentu se zobrazí na klientovi ke kontrole.

13. Uživatel může dokument schválit nebo odmítnout.

14. Klient WCF slouží k odeslání odpovědi na schválení zpět do aplikace Správce schvalování.

Proces schvalování vychází z pohledu aplikace schvalování Manager v zobrazení následujícím způsobem:

1. Klient žádá o účast do systému procesu schvalování.

2. Služba WCF ve Správci schvalování obdrží požadavek, aby byl součástí systému schvalování procesů.

3. Pro klienta je vygenerováno jedinečné ID. Informace o uživateli jsou uloženy v databázi aplikace.

4. Jedinečné ID se pošle zpátky uživateli.

5. Obdrží se žádost o schválení. Správce schvalování provede schvalovací proces.

6. Správce schvalování obdrží žádost o schválení a spustí nový pracovní postup.

7. V závislosti na typu požadavku (jednoduché, kvorum nebo složité) se spustí jiná aktivita.

8. Aktivity Send a Receive se službou Correlation slouží k odeslání žádosti o schválení klientovi ke kontrole a přijetí odpovědi.

9. Výsledek pracovního postupu procesu schválení je odeslán klientovi.

## <a name="using-the-sample"></a>Použití ukázky

##### <a name="to-set-up-the-database"></a>Nastavení databáze

1. Z příkazového řádku sady Visual Studio 2010 otevřeného s oprávněními správce přejděte do této složky DocumentApprovalProcess a spusťte Setup. cmd.

##### <a name="to-set-up-the-application"></a>Nastavení aplikace

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení DocumentApprovalProcess. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Chcete-li spustit řešení, spusťte aplikaci Správce schvalování kliknutím pravým tlačítkem na projekt ApprovalManager v **Průzkumník řešení** a kliknutím na položku **ladit** -> **Spustit** novou instanci z místní nabídky.

    Počkejte, až bude výstup správce, a dejte vám jistotu, že je připravený.

##### <a name="to-run-the-single-approval-scenario"></a>Spuštění jediného scénáře schválení

1. Otevřete příkazový řádek s oprávněním správce.

2. Přejděte do adresáře, který obsahuje řešení.

3. Přejděte do složky ApprovalClient\Bin\Debug a spusťte dvě instance nástroje ApprovalClient. exe.

4. Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .

5. Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**. Pro jednoho klienta použijte `UserType1` a druhý typ `UserType2` .

6. V `UserType1` klientovi vyberte typ jednoho schválení z rozevírací nabídky a zadejte název a obsah dokumentu. Klikněte na **žádost o schválení**.

7. V `UserType2` klientovi se zobrazí dokument, který čeká na schválení. Vyberte ji a stiskněte **schválit** nebo **zamítnout**. Výsledky by se měly zobrazit v `UserType1` klientovi.

##### <a name="to-run-the-quorum-approval-scenario"></a>Spuštění scénáře schválení kvora

1. Otevřete příkazový řádek s oprávněním správce.

2. Přejděte do adresáře, který obsahuje řešení.

3. Přejděte do složky ApprovalClient\Bin\Debug a spusťte tři instance nástroje ApprovalClient. exe.

4. Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .

5. Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**. Pro jedno použití klienta `UserType1` a druhý dva typy `UserType2` .

6. V `UserType1` klientovi vyberte typ schválení kvora z rozevírací nabídky a zadejte název a obsah dokumentu. Klikněte na **žádost o schválení**. To vyžaduje, aby dva `UserType2` klienti schválili nebo odmítli dokument. I když `UserType2` musí oba klienti reagovat, musí schválit dokument, jenom jeden klient, aby ho schválil.

7. V `UserType2` klientech se zobrazí dokument čeká na schválení. Vyberte ji a stiskněte **schválit** nebo **zamítnout**. Výsledky by se měly zobrazit v `UserType1` klientovi.

##### <a name="to-run-the-complex-approval-scenario"></a>Spuštění scénáře komplexního schválení

1. Otevřete příkazový řádek s oprávněním správce.

2. Přejděte do adresáře, který obsahuje řešení.

3. Přejděte do složky ApprovalClient\Bin\Debug a spusťte čtyři instance nástroje ApprovalClient. exe.

4. Klikněte na **Vyhledat**a počkejte, než se aktivuje tlačítko **přihlášení k odběru** .

5. Zadejte libovolné uživatelské jméno a klikněte na **přihlásit k odběru**. Pro jednoho klienta používá nástroj `UserType1` ve dvou typech `UserType2` a při posledním použití `UserType3` .

6. V `UserType1` klientovi vyberte typ jednoho schválení z rozevírací nabídky a zadejte název a obsah dokumentu. Klikněte na **žádost o schválení**.

7. V `UserType2` klientech se zobrazí dokument čeká na schválení. Vyberte ji a stiskněte **schválit**, dokument se předává `UserType3` klientovi.

    Pokud dokument schválí první `UserType2` kvorum, dokument se předává `UserType3` klientovi.

8. Schvalte nebo odmítněte dokument z `UserType3` klienta. Výsledky by se měly zobrazit v `UserType1` klientovi.

##### <a name="to-clean-up"></a>Vyčištění

1. Z příkazového řádku sady Visual Studio 2010 přejděte do složky DocumentApprovalProcess a spusťte Cleanup. cmd.
