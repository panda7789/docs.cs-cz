---
title: Proces schválení dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: dfc2e0a12d053733823427ac50066b1e4a0f97aa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59318465"
---
# <a name="document-approval-process"></a>Proces schválení dokumentu
Tento příklad ukazuje použití mnoha funkcí Windows Workflow Foundation (WF) a Windows Communication Foundation (WCF) společně. Společně implementují scénář proces schválení dokumentu. Klientská aplikace může odesílat dokumenty pro schválení a schválit dokumenty. Aplikace Správce schválení existuje pro usnadnění komunikace mezi klienty a vynucení pravidel procesu schvalování. Proces schválení je pracovní postup, který můžete spustit několik typů schválení. Aktivity slouží k získání jedné schválení, schválení kvora (procento sada schvalovatelů) a komplexní schválení proces, který se skládá z jedné schválení v pořadí a kvora.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Následující obrázek ukazuje pracovní postup procesu schvalování dokumentů:  
  
 ![Pracovní postup procesu schvalování dokumentů](./media/document-approval-process/document-approval-process.jpg)  
  
 Z pohledu klienta schválení zpracování funkce takto:  
  
1. Klient přihlásí k odběru bude uživatel v systému proces schvalování.  
  
2. Klienta WCF se odesílá do služby WCF hostované aplikace schválení správce.  
  
3. Jedinečné ID uživatele je vrácen do klienta. Klienta můžete nyní účastnit schvalovací procesy.  
  
4. Po připojený, klient může odesílat dokument pro schválení pomocí jednoho, kvora nebo komplexní schvalovací procesy.  
  
5. Stisknutí tlačítka v rozhraní klienta spuštění instance pracovního postupu v klientovi hostitele služby pracovního postupu.  
  
6. Pracovní postup odešle žádost o schválení aplikace schválení správce.  
  
7. Pracovní postup správce spustí pracovní postup na svůj vlastní straně k reprezentaci schvalovací proces.  
  
8. Jakmile se spustí pracovní postup schválení správce, se výsledky odesílají zpět do klienta.  
  
9. Klient se zobrazí výsledky.  
  
10. Klient může přijímat žádosti o schválení a reagovat na žádosti v libovolném bodě v čase.  
  
11. Služby WCF hostované na straně klienta může přijímat žádosti o schválení aplikace pro správu schválení panelu.  
  
12. Informace o dokumentu se zobrazí na straně klienta pro kontrolu.  
  
13. Uživatel můžete schválit nebo odmítnout dokumentu.  
  
14. Klienta WCF se používá k odesílání odpovědi na schválení zpět do aplikace schválení správce.  
  
 Z aplikace schválení správce schválení zpracování funkce takto:  
  
1. Klient požádá o se zapojit do systému proces schválení.  
  
2. Služby WCF na schválení správce obdrží žádost jako součást procesu systému schválení.  
  
3. Jedinečné ID je generován pro klienta. Informace o uživateli je uložen v databázi.  
  
4. Jedinečné ID je odeslána zpět uživateli.  
  
5. Žádost o schválení je přijímat. Správce schvalování spustí proces schvalování.  
  
6. Správce schvalování, spouští se nový pracovní postup přijme žádost o schválení.  
  
7. V závislosti na typu požadavku (jednoduchý, kvora nebo komplexní) provádí jiné aktivitě.  
  
8. Odesílání a aktivity Receive s korelací slouží k odeslání žádosti o schválení klienta pro kontrolu a přijetí odpovědi.  
  
9. Výsledek pracovního postupu schvalování procesu posílá do klienta.  
  
## <a name="using-the-sample"></a>Pomocí ukázky  
  
##### <a name="to-set-up-the-database"></a>K nastavení databáze  
  
1. Z příkazového řádku sady Visual Studio 2010 otevřeného s oprávněními správce přejděte na tuto složku DocumentApprovalProcess a spustit Setup.cmd.  
  
##### <a name="to-set-up-the-application"></a>Nastavení aplikace  
  
1. Pomocí sady Visual Studio 2010, otevřete soubor řešení DocumentApprovalProcess.sln.  
  
2. Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3. Spuštění řešení, schválení správce aplikaci spustit kliknutím pravým tlačítkem myši na projekt ApprovalManager v **Průzkumníka řešení** a kliknete na **ladění**->**Start**  novou instanci v místní nabídce.  
  
     Čekat správce výstup s oznámením, že je připravený.  
  
##### <a name="to-run-the-single-approval-scenario"></a>Ke spuštění jedné schválení scénář  
  
1. Otevřete příkazový řádek s oprávněním správce.  
  
2. Přejděte do adresáře, který obsahuje řešení.  
  
3. Přejděte do složky ApprovalClient\Bin\Debug a spusťte dvě instance ApprovalClient.exe.  
  
4. Klikněte na tlačítko **zjistit**, počkejte, dokud **odběru** tlačítko je povolené.  
  
5. Zadejte libovolné uživatelské jméno a klikněte na tlačítko **odběru**. Pro jednoho klienta, použijte `UserType1` a jiný typ `UserType2`.  
  
6. V `UserType1` klienta, vyberte jeden schválení zadejte v rozevírací nabídce a zadejte název dokumentu a obsah. Klikněte na tlačítko **žádost o schválení**.  
  
7. V `UserType2` klient, se zobrazí dokument čeká na schválení. Vyberte ji a stiskněte klávesu **schválit** nebo **odmítnout**. Výsledky by měly zobrazovat `UserType1` klienta.  
  
##### <a name="to-run-the-quorum-approval-scenario"></a>Chcete-li spustit scénář schválení kvora  
  
1. Otevřete příkazový řádek s oprávněním správce.  
  
2. Přejděte do adresáře, který obsahuje řešení.  
  
3. Přejděte do složky ApprovalClient\Bin\Debug a provést tři instance ApprovalClient.exe.  
  
4. Klikněte na tlačítko **zjistit**, počkejte, dokud **odběru** tlačítko je povolené.  
  
5. Zadejte libovolné uživatelské jméno a klikněte na tlačítko **odběru**. Pro jednoho klienta používat `UserType1` a další dva typy `UserType2`.  
  
6. V `UserType1` klienta, vyberte schválení kvora, zadejte v rozevírací nabídce a zadejte název dokumentu a obsah. Klikněte na tlačítko **žádost o schválení**. To, který požaduje dva `UserType2` klienty schválit nebo odmítnout dokumentu. Přestože obě `UserType2` klientů musí odpovědět, jen pro jednoho klienta musí schválit, aby se schválit.  
  
7. V `UserType2` klientů, se zobrazí dokument čeká na schválení. Vyberte ji a stiskněte klávesu **schválit** nebo **odmítnout**. Výsledky by měly zobrazovat `UserType1` klienta.  
  
##### <a name="to-run-the-complex-approval-scenario"></a>Chcete-li spustit scénář komplexní schválení  
  
1. Otevřete příkazový řádek s oprávněním správce.  
  
2. Přejděte do adresáře, který obsahuje řešení.  
  
3. Přejděte do složky ApprovalClient\Bin\Debug a spustit čtyři instancí ApprovalClient.exe.  
  
4. Klikněte na tlačítko **zjistit**, počkejte, dokud **odběru** tlačítko je povolené.  
  
5. Zadejte libovolné uživatelské jméno a klikněte na tlačítko **odběru**. Pro jednoho klienta používat `UserType1`ve dvou používá typ `UserType2`a v posledním `UserType3`.  
  
6. V `UserType1` klienta, vyberte jeden schválení zadejte v rozevírací nabídce a zadejte název dokumentu a obsah. Klikněte na tlačítko **žádost o schválení**.  
  
7. V `UserType2` klientů, se zobrazí dokument čeká na schválení. Vyberte ji a stiskněte klávesu **schválit**, dokument je předán `UserType3` klienta.  
  
     Po prvním schválení dokumentu `UserType2` kvora, dokument je předán `UserType3` klienta.  
  
8. Schválit nebo odmítnout dokumentu z `UserType3` klienta. Výsledky by měly zobrazovat `UserType1` klienta.  
  
##### <a name="to-clean-up"></a>Vyčistit  
  
1. Z příkazového řádku sady Visual Studio 2010 přejděte do složky DocumentApprovalProcess a spusťte Cleanup.cmd.
