---
title: Zabezpečení služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 53f84ad5-1ed1-4114-8d0d-b12e8a021c6e
ms.openlocfilehash: 28c34ecf7d6d781bfa461b2737cb9325a657f47e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43524332"
---
# <a name="securing-workflow-services"></a>Zabezpečení služeb pracovních postupů
V ukázce Zabezpečená služba pracovního postupu najdete v následujících postupech:  
  
-   Vytváření s použitím služby základní pracovní postup <xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply> aktivity.  
  
-   Chcete-li definovat zabezpečené koncové body pro použití službou pracovního postupu pomocí konfigurace Windows Communication Foundation (WCF).  
  
-   Deklarace identity uvnitř vlastní zásady pro vytváření a používání <xref:System.ServiceModel.ServiceAuthorizationManager> k ověřování deklarací identity.  
  
## <a name="demonstrates"></a>Demonstruje  
 Pomocí zabezpečení WCF pro zabezpečení komunikace mezi klientem a služby pracovních postupů, autorizace deklarovaných identit  
  
## <a name="discussion"></a>Diskuse  
 Tento příklad znázorňuje používání infrastruktury zabezpečení WCF pro zabezpečení služby pracovního postupu, stejně jako normální službou WCF. Konkrétně používá vlastní deklarace identity pro autorizaci. V tomto případě používá <xref:System.ServiceModel.WSHttpBinding> a zprávu režim zabezpečení pomocí přihlašovacích údajů Windows.  
  
 Vlastní <xref:System.IdentityModel.Policy.IAuthorizationPolicy> (`CustomNameCheckerPolicy`) ověří uživatelské jméno klienta Windows a pro konkrétní znak. Pokud tento znak je k dispozici, vytvoří a přidá deklaraci do <xref:System.IdentityModel.Policy.EvaluationContext>. Tímto způsobem, vlastní zásady provádí příkaz, který má klient tento znak uživatelské jméno. Tato deklarace identity může být dotazována v celém životním volání. Můžete najít znaku v `Constants.cs`.  
  
 Zásady autorizace hledá deklarace identity uvnitř `SecureWorkFlowAuthZManager`. Pokud se ho najde, vrátí `true` a povolit pracovní postup, aby bylo možné pokračovat. V opačném případě vrátí `false`, což způsobí, že zprávu "Přístup byl odepřen" má být vrácena klientovi. Další deklarace identity jsou k dispozici v kontextu a lze jej prozkoumat také uvnitř `SecureWorkFlowAuthZManager`.  
  
#### <a name="to-run-this-sample"></a>Tuto ukázku spustit  
  
1.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce.  
  
2.  Načíst SecuringWorkflowServices.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
3.  Stiskněte kombinaci kláves CTRL + SHIFT + B pro kompilaci řešení.  
  
4.  Nastavte jako spouštěcí projekt pro řešení projekt služby.  
  
5.  Stisknutím kláves CTRL + F5 ke spuštění služby bez ladění.  
  
6.  Nastavte klientský projekt jako projekt spuštění pro řešení.  
  
7.  Stisknutím kláves CTRL + F5 spusťte klienta bez ladění.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\SecuringWorkflowServices`
