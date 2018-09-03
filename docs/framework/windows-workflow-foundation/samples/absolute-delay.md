---
title: Absolutní prodleva
ms.date: 03/30/2017
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
ms.openlocfilehash: 30719a4340b738a7462584c4dca00f6d5d90ac72
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486099"
---
# <a name="absolute-delay"></a>Absolutní prodleva
Hlavní scénáře pro tuto ukázku spočívá ve zpoždění až do zadaného <xref:System.DateTime> pomocí časovače odolné aplikace pracovního postupu. Tím se liší od použití předdefinované <xref:System.Activities.Statements.Delay> aktivitu jako tento vám pouze umožní, než se dané <xref:System.TimeSpan> (nebo počet minut nebo sekund).  
  
 Některé reálné scénáře, ve kterých chcete rozlišit patří následující:  
  
1.  Chcete-li prodleva odesílání e-mailu pro 30 sekund, ujistěte se, že jste nevytvořili žádné chyby.  
  
2.  Jsou pracují a chcete zpoždění všechny vaše e-mailů do normální pracovních hodin (například 8: 00).  
  
## <a name="demonstrates"></a>Demonstruje  
  
1.  <xref:System.Activities.Statements.DurableTimerExtension> pro implementaci absolutní prodleva  
  
2.  Nastavení trvalosti pomocí <xref:System.Activities.WorkflowApplication> pro trvalý časovače  
  
3.  Použití <xref:System.Activities.NativeActivity%601> pro používání bodů rozšiřitelnosti  
  
4.  Použití <xref:System.Activities.CodeActivity%601> v Connectoru aktivitu  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  Pracovní postup pouze pro XAML  
  
 Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která přijímá <xref:System.DateTime> a trvalý časovače používá k registraci doba zpoždění. Při použití trvalý časovače, je nutné použít <xref:System.Activities.NativeActivity> vytvořte záložku, jak budete muset zaregistrovat tuto záložku pomocí časovače rozšíření. V této ukázce, když vyprší platnost trvalý časovač `OnTimerExpired` metoda bude volána. Ujistěte se, že přidáváte časovače rozšíření v <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> událostí, aby pomocí těchto informací poskytujete modulu runtime. Jenom další podrobnosti implementace je, že budete muset implementovat logiku pro převod z <xref:System.DateTime> k <xref:System.TimeSpan>, protože trvalého časovače trvat pouze <xref:System.DateTime>. Mějte na paměti, že existuje malé zachytí přesnost prováděním  
  
> [!NOTE]
>  Existuje malé ztrátou přesnosti převodem z <xref:System.DateTime> k <xref:System.TimeSpan>.  
  
 Tento příklad také ukazuje, jak zapnout stálost pro <xref:System.Activities.WorkflowApplication>. V tomto konkrétním příkladu použijeme trvalý časovače, ve kterých se data pracovního postupu uvolněných do databáze trvalosti během doby nečinnosti při čekání na časovač vypršení platnosti. Tato implementace lze použít také pro další akce trvalosti. Tento příklad ukazuje, jak nastavit připojovací řetězec trvalost s SQL serverem a tom, jak vytvořit v úložišti instancí, aby bylo možné zachovat data instance pracovního postupu. Logika je k dispozici na tom, jak obnovit pracovní postup po vyvolá událost, díky spustitelné instance pracovního postupu.  
  
 Krocích této ukázce uvidíte, že čas, ve kterém integrované zpoždění zahájí a dokončí, která zase způsobí, že e-mailové zprávy k odeslání. Odtud se zastaví aktivity AbsoluteDelay až do zadaného <xref:System.DateTime> (nebo 0 sekund, pokud <xref:System.DateTime> vypršela platnost) který pak se rozešle e-mail po vypršení platnosti. Tím se zobrazí dvě různé případy integrovaných použití <xref:System.Activities.Statements.Delay> funkce oproti použití AbsoluteDelay aktivity.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že máte SQL Server Express (nebo vyšší) na vašem počítači nainstalovaná  
  
2.  Spustit setup.cmd (z WF/Basic/Services/AbsoluteDelay/CS) [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku vytvořit AbsoluteDelaySampleDB databázi, vytvoření schématu trvalosti a vytvoření logiky trvalosti.  
  
3.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  V aktivitě Delay určete dobu trvání.  
  
5.  Zadejte ExpirationTime AbsoluteDelay aktivity.  
  
6.  Aktualizují se pole SendMailTo SendMailFrom, SendMailSubject, SendMailBody a SmtpHost v aktivita SendMail.  
  
    > [!NOTE]
    >  Pokud se platný hostitel SMTP nezadáte, aplikace vyvolá výjimka SMTP.  
  
7.  Sestavte řešení tak, že vyberete **sestavení**, **sestavit řešení**.  
  
8.  Spuštění řešení stisknutím kombinace kláves **F5**.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
