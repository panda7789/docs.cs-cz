---
title: Vyrovnávací paměť přijímat
ms.date: 03/30/2017
ms.assetid: 9d46d9b9-96c9-4531-9695-ab526b4d704a
ms.openlocfilehash: b95577c71493275f30703b4366fab32a51097bd2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43526801"
---
# <a name="buffered-receive"></a>Vyrovnávací paměť přijímat
Tento příklad ukazuje, jak vytvořit a nakonfigurovat funkci ve vyrovnávací paměti příjmu ve Windows Workflow Foundation (WF). Vyrovnávací paměť přijímat umožňuje vytvořit pracovní postup k vytvoření pracovního postupu bez nutnosti starat o pořadí, ve kterém jsou zprávy přijímány. Funkce ve vyrovnávací paměti receive ukládá do vyrovnávací paměti zpráv místně a poskytnout je, když pracovní postup je připravený je přijmout.  
  
## <a name="demonstrates"></a>Demonstruje  
 Zpracování zpráv mimo pořadí pomocí uložených do vyrovnávací paměti přijímat pomocí aktivit zasílání zpráv.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`  
  
## <a name="discussion"></a>Diskuse  
 V této ukázce je implementováno pomocí služby Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] a obsahuje posloupnost <xref:System.ServiceModel.Activities.Receive> aktivity. Tento pracovní postup modely jednoduché půjčky schvalovací proces, který tam, kde pracovní postup očekává tři oznámení o půjčku ke schválení. Windows Communication Foundation (WCF) klientská aplikace odešle tři korelační oznámení v obráceném pořadí, než co služba očekává. Protože funkce ve vyrovnávací paměti receive je zapnutá na službu, každou zprávu mimo pořadí ukládány do vyrovnávací paměti na službu a zpracovat, protože pracovní postup bude připravený je přijmout.  
  
 Funkce ve vyrovnávací paměti příjmu vyžaduje <xref:System.ServiceModel.Activities.ReceiveContent> podporu – od vazby, proto službu používá <xref:System.ServiceModel.NetMsmqBinding>. Žádná zvláštní konfigurace je potřebná pro svázání, takže se používají výchozí hodnoty.  
  
```xml  
<endpoint address ="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                  binding="netMsmqBinding"  
                  contract="ILoanService"/>  
```  
  
 Služba také poskytuje metadata pro službu pomocí <xref:System.ServiceModel.Description.ServiceMetadataBehavior>.  
  
 Podobně je koncový bod klienta konfigurovat pomocí <xref:System.ServiceModel.NetMsmqBinding>. Kód klienta a konfigurace je generována pomocí **přidat odkaz na službu** funkce sady Visual Studio. V následujícím příkladu je koncový bod generovaného klienta v souboru App.config.  
  
```xml  
<endpoint address="net.msmq://localhost/private/LoanService/Service1.xamlx"  
                binding="netMsmqBinding" bindingConfiguration="NetMsmqBinding_ILoanService"  
                contract="ServiceReference1.ILoanService" name="NetMsmqBinding_ILoanService" />  
```  
  
 Tato ukázka vyžaduje, že jsou povoleny následující součásti Windows:  
  
1.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)]  
  
2.  [!INCLUDE[iis60](../../../../includes/iis60-md.md)] Kompatibilita správy, metabáze a konfigurace kompatibility  
  
3.  Webové služby, funkce pro vývoj aplikací a ASP.NET  
  
4.  Server Microsoft zpráv fronty (MSMQ)  
  
#### <a name="to-set-up-and-build-the-sample"></a>K nastavení a sestavit ukázku  
  
1.  Na [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek, registrace technologie ASP.NET tak, že zadáte `aspnet_regiis –I` a stiskněte klávesu ENTER.  
  
2.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] jako správce.  
  
3.  Otevřete LoanService.sln.  
  
4.  Když se zobrazí výzva, pokud chcete vytvořit virtuální adresář pro projekt LoanService, vyberte **Ano**.  
  
#### <a name="to-set-up-the-service-queues"></a>Nastavení služby front  
  
1.  Stisknutím klávesy F5 spusťte aplikaci LoanClient, která vytvoří front a aktivuje služby definované v Service1.xamlx.  
  
2.  Otevřít **Správa počítače** konzoly spuštěním Compmgmt.msc z příkazového řádku.  
  
3.  V **Správa počítače** rozbalte **služby**, **aplikací**, **služby Řízení front zpráv**, **soukromé fronty** .  
  
4.  Klikněte pravým tlačítkem na loanservice/service1.xamlx fronty a vyberte **vlastnosti**.  
  
5.  Vyberte **zabezpečení** karta a přidat **přijímá zprávy všem**, **prohlížet zprávy** a **poslat zprávu** oprávnění.  
  
6.  Otevřít [!INCLUDE[iis60](../../../../includes/iis60-md.md)] správce.  
  
7.  Přejděte do **Server**, **lokality**, **výchozí webová stránka**, **privátní**, **LoanService** a vyberte  **Rozšířené možnosti**  
  
8.  Změnit **povolené protokoly** bude **http**, **net.msmq**.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Přejděte do http://localhost/private/loanservice/service1.xamlx zajistit, že je služba spuštěna.  
  
2.  Stisknutím klávesy F5 spusťte aplikaci LoanClient. Po dokončení pracovního postupu by měl být soubor s příponou out.txt uložen C:\Inbox, který obsahuje výsledek výměně zpráv.  
  
#### <a name="to-clean-up"></a>Vyčistit  
  
1.  Otevřít **Správa počítače** konzoly spuštěním Compmgmt.msc z příkazového řádku.  
  
2.  Rozbalte **služby** a **aplikací**, **služby Řízení front zpráv**, **soukromé fronty**.  
  
3.  Odstraňte frontu loanservice/service1.xamlx.  
  
4.  Odeberte adresář C:\Inbox.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\BufferedReceive`
