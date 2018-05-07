---
title: Trvanlivý duplexní přenos
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 91490eb3ee6c11f29bb49d8343b807e74e8d3bc2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="durable-duplex"></a>Trvanlivý duplexní přenos
Tento příklad ukazuje, jak připravit a nakonfigurovat systém exchange trvanlivý duplexní zpráv pomocí aktivity zasílání zpráv v systému Windows Workflow Foundation (WF). Trvanlivý duplexní zpráva exchange je obousměrný zpráva systému exchange, který probíhá po dlouhou dobu. Doba platnosti výměny zpráv může být delší než komunikační kanál životnost a doba platnosti v paměti instancí služby.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V této ukázce jsou dvě služby Windows Communication Foundation (WCF) implementovaná pomocí modelu Windows Workflow Foundation nakonfigurované tak, aby měl exchange trvanlivý duplexní zprávy. Trvanlivý duplexní zpráva exchange se skládá ze dvou jednosměrný zprávy přes služby MSMQ a korelační pomocí [.NET kontextová výměna](http://go.microsoft.com/fwlink/?LinkID=166059). Odeslání zpráv pomocí <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> aktivity zasílání zpráv. Kontextová výměna .NET je slouží k určení adresu zpětné volání na odeslané zprávy. Obě služby jsou hostované pomocí služby Aktivace procesů systému Windows (WAS) a jsou nakonfigurovány pro zapnout stálost instancí služby.  
  
 První službě (Service1.xamlx) odešle požadavek na službu odeslání (Service2.xamlx) nějakou práci. Po dokončení práce Service2.xamlx odešle oznámení zpátky do Service1.xamlx indikující, že práce na byla dokončena. Konzolové aplikace pracovního postupu nastaví fronty, které služby jsou naslouchá na a odešle zprávu počáteční počáteční aktivovat Service1.xamlx. Jakmile Service1.xamlx obdrží oznámení z Service2.xamlx dokončí požadovanou pracovní, Service1.xamlx výsledek uloží do souboru XML. Při čekání na zprávu zpětného volání, Service1.xamlx potrvají jeho stav instance pomocí výchozího <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>. Service2.xamlx trvá jeho stav instance jako součást dokončení práce požadoval Service1.xamlx.  
  
 Ke konfiguraci služby na používání rozhraní .NET kontextová výměna přes služby MSMQ, obě služby jsou nakonfigurovány pro použití vlastní vazby, která se skládá z <xref:System.ServiceModel.Channels.ContextBindingElement> a <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>. Je zadaný adresu zpětné volání <xref:System.ServiceModel.Channels.ContextBindingElement> a je součástí všech zpráv odeslaných použití vlastní vazby v hlavičce kontext zpětného volání. Následující příklad kódu definuje vlastní vazby.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          …  
          <bindings>  
               <customBinding>  
                    <binding name="netMsmqContextBinding">  
                         <context clientCallbackAddress="net.msmq://localhost/private/DurableDuplex/Service1.xamlx"/>  
                         <msmqTransport exactlyOnce="False">  
                              <msmqTransportSecurity msmqAuthenticationMode="None" msmqProtectionLevel="None"/>  
                         </msmqTransport>  
                    </binding>  
               </customBinding>  
          </bindings>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  Vazba používá tato ukázka není zabezpečený. Při nasazování aplikace byste měli nakonfigurovat vaše vazby v závislosti na požadavcích zabezpečení vaší aplikace.  
  
> [!NOTE]
>  Fronty použít v této ukázce nejsou transakcí. Příklad, který ukazuje, jak nastavit [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] výměnu pomocí transakce front zpráv najdete v tématu [aktivace MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) ukázka.  
  
 Zpráva odeslaná Service1.xamlx Service2.xamlx odeslána, koncový bod klienta nakonfigurovanou adresu Service2.xamlx a vlastní vazby pomocí definována dříve. Zpětné volání z Service2.xamlx Service1.xamlx je odeslána pomocí koncový bod klienta s žádnou explicitně nakonfigurovanou adresu, protože adresa je převzat ze zpětného volání kontextu poslal Service1.xamlx. Následující příklad kódu definuje koncové body klientů.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
     <system.serviceModel>  
          …  
          <client>  
               <endpoint address="net.msmq://localhost/private/DurableDuplex/Service2.xamlx" binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="IDoWork"/>  
               <endpoint binding="customBinding" bindingConfiguration="netMsmqContextBinding" contract="INotify"/>  
          </client>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 Následující příklad kódu zpřístupní koncové body pomocí tento vlastní vazby změnou výchozí mapování protokolu pro základní adresy net.msmq používat tento vlastní vazby.  
  
```xml  
<configuration>  
     <system.serviceModel>  
          <protocolMapping>  
               <add scheme="net.msmq" binding="customBinding" bindingConfiguration="netMsmqContextBinding"/>  
          </protocolMapping>  
          …  
     </system.serviceModel>  
</configuration>  
```  
  
 Následující příklad kódu povolí trvalost pro obě služby přidáním <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování služby a zadat připojovací řetězec pro databázi trvalost.  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
    <system.serviceModel>  
          …  
          <behaviors>  
               <serviceBehaviors>  
                    <behavior>  
                         <serviceDebug includeExceptionDetailInFaults="True"/>  
                         <serviceMetadata httpGetEnabled="True"/>  
                         <sqlWorkflowInstanceStore connectionString="Data Source=.\SQLEXPRESS;Initial Catalog=DefaultSampleStore;Integrated Security=True"/>  
                    </behavior>  
               </serviceBehaviors>  
          </behaviors>  
     </system.serviceModel>  
</configuration>  
```  
  
## <a name="system-requirements"></a>Požadavky na systém  
 Tato ukázka vyžaduje následující součásti.  
  
1.  Internetová informační služba.  
  
2.  Internetová informační služba -> Kompatibilita správy služby IIS 6.0 -> Konfigurace Kompatibilita metabáze služby IIS a služby IIS 6.0.  
  
3.  Webové služby -> vývoj aplikací funkce -> technologie ASP.NET.  
  
4.  Server Microsoft zprávu fronty (MSMQ).  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Nastavte databázi trvalosti a adresáři výsledky.  
  
    1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
    2.  Přejděte do složky, aby tato ukázka a spusťte Setup.cmd.  
  
2.  Nastavte virtuální aplikace.  
  
    1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazový řádek, zaregistrovat ASP.NET tak, že spustíte následující příkaz.  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce kliknutím pravým tlačítkem na [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a výběrem **spustit jako správce**.  
  
    3.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor DurableDuplex.sln.  
  
3.  Nastavení fronty služby service.  
  
    1.  Spuštění klienta DurableDuplex, stisknutím klávesy F5.  
  
    2.  Otevřete **Správa počítače** konzoly spuštěním `Compmgmt.msc` z příkazového řádku.  
  
    3.  Rozbalte položku **služby a aplikace**, **služby Řízení front zpráv**. **Soukromé fronty**.  
  
    4.  Klikněte pravým tlačítkem na durableduplex/service1.xamlx a durableduplex/service2.xamlx front a vyberte **vlastnosti**.  
  
    5.  Vyberte **zabezpečení** kartě a povolit **Everyone přijímat zprávy**, **prohlížet zprávy** a **odeslat zprávu** oprávnění pro obě fronty.  
  
    6.  Otevřete Správce Internetové informační služby (IIS).  
  
    7.  Přejděte do **Server**, **lokality**, **výchozí web**, **privátní**, **trvanlivý duplexní** a vyberte **Rozšířené možnosti**.  
  
    8.  Změna **povolené protokoly** k **http,net.msmq**.  
  
4.  Spusťte ukázku.  
  
    1.  Přejděte do http://localhost/private/durableduplex/service1.xamlx a http://localhost/private/durableduplex/service2.xamlx zajistit, že jsou obě služby spuštěny.  
  
    2.  Stisknutím klávesy F5 spusťte DurableDuplexClient.  
  
         Po dokončení exchange trvanlivý duplexní zpráva result.xml soubor je uložen ve složce C:\Inbox a obsahuje výsledek zprávy exchange.  
  
#### <a name="to-cleanup-optional"></a>Pro čištění (volitelné)  
  
1.  Spusťte Cleanup.cmd.  
  
    1.  Otevřete [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
    2.  Přejděte do složky, aby tato ukázka a spusťte Cleanup.cmd.  
  
2.  Odeberte virtuální aplikace pro služby.  
  
    1.  Otevřete Správce Internetové informační služby (IIS) spuštěním `Inetmgr.exe` z příkazového řádku.  
  
    2.  Přejděte na výchozí web a odebrat **privátní** virtuální adresář.  
  
3.  Odeberte nastavení pro tato ukázka fronty.  
  
    1.  Otevřete konzolu pro správu počítače spuštěním `Compmgmt.msc` z příkazového řádku.  
  
    2.  Rozbalte položku **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.  
  
    3.  Odstraňte durableduplex/service1.xamlx a durableduplex/service2.xamlx fronty.  
  
4.  Odeberte adresář C:\Inbox.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`