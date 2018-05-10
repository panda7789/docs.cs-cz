---
title: Proces schválení dokumentu
ms.date: 03/30/2017
ms.assetid: 9b240937-76a7-45cd-8823-7f82c34d03bd
ms.openlocfilehash: c28dafd3b0a1cb6dbee37fed2b3df8923ccd82c8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="document-approval-process"></a>Proces schválení dokumentu
Tento příklad znázorňuje použití mnoha funkcí Windows Workflow Foundation (WF) a Windows Communication Foundation (WCF) společně. Společně se implementaci procesu scénáře schválení dokumentu. Klientská aplikace může odesílat dokumenty k schválení a schválit dokumenty. Aplikace Správce schválení existuje pro usnadnění komunikace mezi klienty a vynucování pravidel procesu schvalování. Proces schválení je pracovní postup, který můžete spustit několik typů schválení. Aktivity existovat získat jeden schválení, schválení kvora (procento sadu schvalovatelů) a komplexní schválení proces, který se skládá z jedné schválení v pořadí a kvora.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\DocumentApprovalProcess`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Následující obrázek ukazuje pracovní postup procesu schvalování dokumentů.  
  
 ![Pracovní postup procesu schvalování dokumentů](../../../../docs/framework/windows-workflow-foundation/samples/media/approvalprocess.jpg "ApprovalProcess")  
  
 Z pohledu klienta schválení procesu funkce následujícím způsobem:  
  
1.  Klient jako odběratel u být uživatelem v systému procesu schvalování.  
  
2.  Klienta WCF odešle do služby WCF hostované aplikace schválení správce.  
  
3.  Jedinečné ID uživatele je vrácen do klienta. Klienta můžete nyní účastnit schvalovací procesy.  
  
4.  Po připojený, klient může odesílat dokumentu pro schválení pomocí jednoho, kvora nebo komplexní schvalovací procesy.  
  
5.  Stisknutí tlačítka v rozhraní klienta od instance pracovního postupu v klientovi hostitele služby pracovního postupu.  
  
6.  Pracovní postup odešle žádost o schválení aplikace schválení správce.  
  
7.  Pracovní postup správce spustí pracovní postup na vlastní straně představují proces schvalování.  
  
8.  Jakmile se spustí pracovní postup schválení správce, výsledky se odesílají zpět do klienta.  
  
9. Klient se zobrazí výsledky.  
  
10. Klient může obdrží žádost o schválení a odpovědět na požadavek v libovolném bodě v čase.  
  
11. Služby WCF hostované na straně klienta může přijímat žádost o schválení od správce aplikace schválení.  
  
12. Dokument informace jsou poskytovány na straně klienta ke kontrole.  
  
13. Uživatele můžete schválit nebo odmítnout dokumentu.  
  
14. Klienta WCF se používá k odesílání odpověď na žádost o zpět do aplikace schválení správce.  
  
 Z aplikace schválení správce schválení procesu funkce následujícím způsobem:  
  
1.  Klient požádá o zapojit do procesu systému schválení.  
  
2.  Služby WCF na schválení správce přijme požadavek jako součást procesu systému schválení.  
  
3.  Jedinečné ID se generuje pro klienta. Uživatelské informace jsou uloženy v databázi.  
  
4.  Jedinečné ID budou odeslána zpět do uživatele.  
  
5.  Žádost o schválení je přijmout. Správce schvalování spustí proces schvalování.  
  
6.  Žádost o schválení byl přijat schválení správcem, spouštění nového pracovního postupu.  
  
7.  V závislosti na typu požadavku (jednoduchý, kvora nebo komplexní) se spustí jiné aktivitě.  
  
8.  Odesílání a příjmu aktivity s korelací se používají k poslat žádost o schválení klienta ke kontrole a přijímat odpovědi.  
  
9. Výsledek procesu pracovního postupu schválení je odeslat klientovi.  
  
## <a name="using-the-sample"></a>Pomocí vzorku  
  
##### <a name="to-set-up-the-database"></a>K nastavení databáze  
  
1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] otevřít příkazový řádek s oprávněními správce, přejděte do této složky DocumentApprovalProcess a spusťte Setup.cmd.  
  
##### <a name="to-set-up-the-application"></a>Nastavení aplikace  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení DocumentApprovalProcess.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, Správce schvalování aplikaci spustit kliknutím pravým tlačítkem myši na projekt ApprovalManager **Průzkumníku řešení** a kliknutím na **ladění**->**Start**  nové instance z místní nabídky.  
  
     Počkejte manažera výstup do vám oznamuje, že je připravený.  
  
##### <a name="to-run-the-single-approval-scenario"></a>Ke spuštění jedné schválení scénář  
  
1.  Otevřete příkazový řádek s oprávněním správce.  
  
2.  Přejděte do adresáře, který obsahuje řešení.  
  
3.  Přejděte do složky ApprovalClient\Bin\Debug a provést dvě instance ApprovalClient.exe.  
  
4.  Klikněte na tlačítko **zjistit**, počkejte **přihlášení k odběru** tlačítko je k dispozici.  
  
5.  Zadejte libovolné uživatelské jméno a klikněte na **přihlášení k odběru**. Pro jednoho klienta, použijte `UserType1` a v případě druhého typu `UserType2`.  
  
6.  V `UserType1` klienta, vyberte jeden schválení typu z rozevírací nabídky a zadejte název dokumentu a obsahu. Klikněte na tlačítko **požádat o schválení**.  
  
7.  V `UserType2` se zobrazí dokument čeká na schválení klienta. Vyberte ho a stiskněte klávesu **schválit** nebo **odmítnout**. Výsledky by měl zobrazit v `UserType1` klienta.  
  
##### <a name="to-run-the-quorum-approval-scenario"></a>Ke spuštění scénáře schválení kvora  
  
1.  Otevřete příkazový řádek s oprávněním správce.  
  
2.  Přejděte do adresáře, který obsahuje řešení.  
  
3.  Přejděte do složky ApprovalClient\Bin\Debug a provést tři instance ApprovalClient.exe.  
  
4.  Klikněte na tlačítko **zjistit**, počkejte **přihlášení k odběru** tlačítko je k dispozici.  
  
5.  Zadejte libovolné uživatelské jméno a klikněte na **přihlášení k odběru**. Pro jednoho klienta používat `UserType1` a další dva typy `UserType2`.  
  
6.  V `UserType1` klienta, vyberte schválení kvora typu z rozevírací nabídky a zadejte název dokumentu a obsahu. Klikněte na tlačítko **požádat o schválení**. To požadavky, které dva `UserType2` klienty schválit nebo odmítnout dokumentu. Při obě `UserType2` klienti musí odpovědět, jen jeden klientský musí schválit v dokumentu ji ke schválení.  
  
7.  V `UserType2` klientů, se zobrazí dokument čeká na schválení. Vyberte ho a stiskněte klávesu **schválit** nebo **odmítnout**. Výsledky by měl zobrazit v `UserType1` klienta.  
  
##### <a name="to-run-the-complex-approval-scenario"></a>Ke spuštění scénář komplexní schválení  
  
1.  Otevřete příkazový řádek s oprávněním správce.  
  
2.  Přejděte do adresáře, který obsahuje řešení.  
  
3.  Přejděte do složky ApprovalClient\Bin\Debug a provést čtyři instance ApprovalClient.exe.  
  
4.  Klikněte na tlačítko **zjistit**, počkejte **přihlášení k odběru** tlačítko je k dispozici.  
  
5.  Zadejte libovolné uživatelské jméno a klikněte na **přihlášení k odběru**. Pro jednoho klienta používat `UserType1`v dva používá typ `UserType2`a v posledního použití `UserType3`.  
  
6.  V `UserType1` klienta, vyberte jeden schválení typu z rozevírací nabídky a zadejte název dokumentu a obsahu. Klikněte na tlačítko **požádat o schválení**.  
  
7.  V `UserType2` klientů, se zobrazí dokument čeká na schválení. Vyberte ho a stiskněte klávesu **schválit**, dokument je předána `UserType3` klienta.  
  
     Pokud dokument schválí první `UserType2` kvora, dokument je předána `UserType3` klienta.  
  
8.  Schválit nebo odmítnout dokumentu z `UserType3` klienta. Výsledky by měl zobrazit v `UserType1` klienta.  
  
##### <a name="to-clean-up"></a>Vyčistěte  
  
1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek, přejděte do složky DocumentApprovalProcess a spusťte Cleanup.cmd.