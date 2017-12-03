---
title: "Absolutní zpoždění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b483139a-39bb-4560-8003-8969a8fc2cd1
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94eb9f401786ef05beaa51077ff4ddc170595752
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="absolute-delay"></a>Absolutní zpoždění
Hlavní scénáře pro tato ukázka má počkat, dokud zadané <xref:System.DateTime> pomocí trvanlivý časovačů v aplikaci pracovního postupu. To se liší od pomocí integrovaných <xref:System.Activities.Statements.Delay> aktivitu jako to bude umožňují pouze zpoždění pro danou <xref:System.TimeSpan> (nebo počet minut nebo sekund).  
  
 Některé reálnými scénáře, ve kterých můžete chtít provést na těchto rozdílech patří:  
  
1.  Chcete-li prodleva odesílání pošty po dobu 30 sekund a ujistěte se, že jste nepodali případné chyby.  
  
2.  Jsou nadměrně a chcete všechny vaše e-mailů zpoždění až normální pracovní dobu (například 8: 00).  
  
## <a name="demonstrates"></a>Demonstruje  
  
1.  <xref:System.Activities.Statements.DurableTimerExtension>pro implementaci absolutní zpoždění  
  
2.  Nastavení pomocí trvalosti <xref:System.Activities.WorkflowApplication> pro odolná časovače  
  
3.  Použití <xref:System.Activities.NativeActivity%601> pro používání body rozšiřitelnosti  
  
4.  Použití <xref:System.Activities.CodeActivity%601> v Connectoru aktivitu  
  
5.  <xref:System.Activities.Statements.Delay>  
  
6.  Pouze XAML pracovního postupu  
  
 Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která přebírá <xref:System.DateTime> a používá k registraci zpoždění Doba trvání trvanlivý časovače. Pokud používáte trvanlivý časovače, je nutné použít <xref:System.Activities.NativeActivity> vytvořte záložku, jak budete muset zaregistrovat tuto záložku s příponou časovače. V této ukázce, když časovač trvanlivý vyprší `OnTimerExpired` volání metody. Ujistěte se, že přidáváte časovače rozšíření v <xref:System.Activities.NativeActivity%601.CacheMetadata%2A> událostí zajistit tím modul runtime s těmito informacemi. Jenom jiné implementace podrobností je, že je nutné implementovat logiku pro převod z <xref:System.DateTime> k <xref:System.TimeSpan>, jak trvanlivý časovače trvat jenom <xref:System.DateTime>. Všimněte si, že malé chybě přesnost nástrojem  
  
> [!NOTE]
>  Existuje malé ztrátu přesnosti převodem z <xref:System.DateTime> k <xref:System.TimeSpan>.  
  
 Tento příklad také ukazuje, jak zapnout stálost pro <xref:System.Activities.WorkflowApplication>. Tato ukázka konkrétní použijeme trvanlivý časovače, ve kterých budou data pracovního postupu uvolněna do databáze trvalost během doby nečinnosti při čekání na časovač vyprší. Tato implementace mohou sloužit také pro další akce trvalost. Tento příklad ukazuje, jak nastavit připojovací řetězec trvalost s SQL serverem a postup vytvoření instance úložiště s cílem zachovat data instance pracovního postupu. Logika je k dispozici o tom, jak obnovit pracovního postupu, jakmile se vyvolá událost, takže je spustitelného k instanci pracovního postupu.  
  
 Krocích tuto ukázku, zobrazí se, že doba, ve kterém předdefinované zpoždění začne a dokončení, který zase způsobí, že e-mailová zpráva k odeslání. Z tohoto místa se zastaví AbsoluteDelay aktivity do zadané <xref:System.DateTime> (nebo 0 sekund, pokud <xref:System.DateTime> vypršela platnost) který naopak k odeslání e-mailu po vypršení platnosti. Tato rutina ukáže případech předdefinované použití dvou různých <xref:System.Activities.Statements.Delay> funkce a kdy AbsoluteDelay aktivitu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že máte systému SQL Server Express (nebo novější), nainstalovaný na počítači  
  
2.  Spustit setup.cmd (z WF/Basic/Services/AbsoluteDelay/CS) [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku AbsoluteDelaySampleDB databázi vytvořit, vytvořit schéma trvalosti a vytvořit logiku trvalost.  
  
3.  Otevřete řešení v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
4.  Zadejte dobu trvání aktivity zpoždění.  
  
5.  Zadejte ExpirationTime AbsoluteDelay aktivity.  
  
6.  Aktualizujte pole SendMailTo, SendMailFrom, SendMailSubject, SendMailBody a SmtpHost SendMail aktivity.  
  
    > [!NOTE]
    >  Pokud nezadáte platný hostitel SMTP, vyvolá aplikace SMTP výjimka.  
  
7.  Sestavte řešení výběrem **sestavení**, **sestavit řešení**.  
  
8.  Spuštění řešení stisknutím **F5**.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\AbsoluteDelay`
