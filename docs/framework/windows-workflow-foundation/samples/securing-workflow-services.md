---
title: "Zabezpečení služeb pracovních postupů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 601a7312bdf88ac4915478b6d8fb0626b645a0b1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="securing-workflow-services"></a>Zabezpečení služeb pracovních postupů
Ukázka zabezpečené služby pracovního postupu ukazuje následujících postupů:  
  
-   Vytváření s použitím služby základní pracovní postup <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity.  
  
-   Pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] konfiguraci, která definuje zabezpečení koncových bodů pro použití službou pracovního postupu.  
  
-   Deklarace identity uvnitř vlastní zásady pro vytváření a používání <xref:System.ServiceModel.ServiceAuthorizationManager> ověřit deklarace identity.  
  
## <a name="demonstrates"></a>Demonstruje  
 Pomocí zabezpečení WCF pro zabezpečení komunikace mezi klientem a službou pracovního postupu, na základě deklarací autorizace  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad znázorňuje použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Infrastruktura zabezpečení pro zabezpečení služby pracovního postupu, stejně jako normální [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby. Konkrétně používá vlastních deklarací identity pro ověřování. V takovém případě se použije <xref:System.ServiceModel.WSHttpBinding> a zpráv režim zabezpečení pomocí pověření systému Windows.  
  
 Vlastní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) ověří uživatelské jméno systému Windows klienta a pro konkrétní znak. Pokud se nachází tento znak, vytvoří a přidá se <xref:System.IdentityModel.Policy.EvaluationContext>. Díky tomu vlastní zásady je provedení příkazu, klient má tento znak v uživatelské jméno. Tento požadavek můžete položit dotaz na po celou dobu volání. Můžete najít tento znak v `Constants.cs`.  
  
 Zásady autorizace hledá deklarace identity uvnitř `SecureWorkFlowAuthZManager`. Pokud najde ho, vrátí `true` a povolit v pracovním postupu pokračovat. Funkce `false`, což způsobí, že zpráva o odepření přístupu má být vrácen do klienta. Další deklarace identity jsou k dispozici v kontextu a může být prověřen také uvnitř `SecureWorkFlowAuthZManager`.  
  
#### <a name="to-run-this-sample"></a>Chcete tuto ukázku spustit  
  
1.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce.  
  
2.  Načíst SecuringWorkflowServices.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Stisknutím kombinace kláves CTRL + SHIFT + B řešení zkompilovat.  
  
4.  Nastavte projekt služby jako spuštění projektu pro řešení.  
  
5.  Stisknutím CTRL + F5 a spusťte službu bez ladění.  
  
6.  Nastavte klientského projektu jako spuštění projektu pro řešení.  
  
7.  Stisknutím CTRL + F5 a spusťte službu klienta bez ladění.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
