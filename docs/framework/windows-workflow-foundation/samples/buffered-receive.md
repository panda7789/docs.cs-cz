---
title: Uložená do vyrovnávací paměti přijímat
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: abec64433d10a23dca6186c6c9a553bbed12a017
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="buffered-receive"></a>Uložená do vyrovnávací paměti přijímat
Tento příklad ukazuje, jak nastavit a konfigurovat funkci vyrovnávací pamětí příjmu v systému Windows Workflow Foundation (WF). Uložená do vyrovnávací paměti přijímat umožňuje autorovi pracovní postup vytvoření pracovního postupu bez nutnosti starat o pořadí, ve kterém jsou přijaty zprávy. Funkci vyrovnávací pamětí příjmu vyrovnávacích pamětí zpráv místně a doručí je, když pracovní postup je připravený je přijmout.  
  
## <a name="demonstrates"></a>Demonstruje  
 Zpracování zpráv mimo pořadí pomocí uložených do vyrovnávací paměti, zobrazí se aktivity zasílání zpráv.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>Diskusní  
 V této ukázce [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby je implementovaná pomocí [!INCLUDE[wf1](../../../../includes/wf1-md.md)] a má posloupnost <xref:System.ServiceModel.Activities.Receive> aktivity. Tento pracovní postup modelů proces schválení jednoduché úvěr tam, kde pracovního postupu očekává tři oznámení o úvěr schválení. A [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klientská aplikace odešle tři korelační oznámení v obráceném pořadí, než co služba očekává. Protože funkce receive ve vyrovnávací paměti je zapnutá ve službách, každou zprávu mimo pořadí uložená do vyrovnávací paměti na službu a zpracovat jako pracovní postup bude připravený je přijmout.  
  
 Funkce vyrovnávací pamětí příjmu vyžaduje <xref:System.ServiceModel.Activities.ReceiveContent> podpory z vazby, proto služba používá <xref:System.ServiceModel.NetMsmqBinding>. Žádná speciální konfigurace je požadované pro vazbu, takže se používají výchozí hodnoty.  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 Služba také poskytuje metadata pro používání služby <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
 Podobně je koncový bod klient konfigurován pomocí <xref:System.ServiceModel.NetMsmqBinding>. Kód klienta a konfigurace je generována pomocí **přidat odkaz na službu** funkce sady Visual Studio. V následujícím příkladu je koncový bod generovaného klienta v souboru App.config.  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 Tato ukázka vyžaduje, že jsou povoleny následující součásti systému Windows:  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Kompatibilita správy metabáze a kompatibilita konfigurace  
  
3.  Webové služby, funkce pro vývoj aplikací a ASP.NET  
  
4.  Server Microsoft zpráv fronty (MSMQ)  
  
#### <a name="to-set-up-and-build-the-sample"></a>Jak nastavit a sestavit ukázku  
  
1.  V [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek, zaregistrovat ASP.NET tak, že zadáte `aspnet_regiis –I` a stiskněte klávesu ENTER.  
  
2.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako správce.  
  
3.  Otevřete LoanService.sln.  
  
4.  Když se zobrazí dotaz, pokud chcete vytvořit virtuální adresáře pro LoanService projekt, vyberte **Ano**.  
  
#### <a name="to-set-up-the-service-queues"></a>Nastavení fronty služby service  
  
1.  Stisknutím klávesy F5 spusťte LoanClient aplikace, která vytvoří fronty a aktivuje služby definované v Service1.xamlx.  
  
2.  Otevřete **Správa počítače** konzoly spuštěním Compmgmt.msc z příkazového řádku.  
  
3.  V **Správa počítače** rozbalte **služby**, **aplikace**, **služby Řízení front zpráv**, **soukromé fronty** .  
  
4.  Klikněte pravým tlačítkem na fronty loanservice/service1.xamlx a vyberte **vlastnosti**.  
  
5.  Vyberte **zabezpečení** a přidejte **Everyone obdrží zprávu**, **prohlížet zprávy** a **odeslat zprávu** oprávnění.  
  
6.  Otevřete [!INCLUDE[iis60](../../../../includes/iis60-md.md)] správce.  
  
7.  Přejděte do **Server**, **lokality**, **výchozí web**, **privátní**, **LoanService** a vyberte  **Rozšířené možnosti**  
  
8.  Změna **povolené protokoly** být **http**, **net.msmq**.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Přejděte do http://localhost/private/loanservice/service1.xamlx zajistit, že je služba spuštěná.  
  
2.  Stisknutím klávesy F5 spusťte aplikaci LoanClient. Po dokončení pracovního postupu by měl být uložen soubor out.txt C:\Inbox obsahující výsledek výměny zpráv.  
  
#### <a name="to-clean-up"></a>Vyčistěte  
  
1.  Otevřete **Správa počítače** konzoly spuštěním Compmgmt.msc z příkazového řádku.  
  
2.  Rozbalte položku **služby** a **aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.  
  
3.  Odstraňte loanservice/service1.xamlx.  
  
4.  Odeberte adresář C:\Inbox.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
