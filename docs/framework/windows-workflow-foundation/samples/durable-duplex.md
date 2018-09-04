---
title: Trvanlivý duplexní přenos
ms.date: 03/30/2017
ms.assetid: 4e76d1a1-f3d8-4a0f-8746-4a322cdff6eb
ms.openlocfilehash: 107c617fa4a8ee0279dcaa07e495587c617b866e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513350"
---
# <a name="durable-duplex"></a>Trvanlivý duplexní přenos
Tento příklad ukazuje, jak vytvořit a nakonfigurovat exchange zpráv trvalý duplexní pomocí aktivit zasílání zpráv ve Windows Workflow Foundation (WF). Výměna zpráv trvalý duplexní je obousměrný zprávy serveru exchange, která probíhá přes dlouhou dobu. Doba života výměny zpráv může být delší než životnost komunikační kanál a v paměti dobu životnosti instance služby.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V této ukázce jsou nakonfigurovány dvě služby Windows Communication Foundation (WCF), které jsou implementované pomocí programovacího modelu Windows Workflow Foundation na trvalý duplexní zprávy exchange. Výměna zpráv trvalý duplexní se skládá ze dvou jednosměrné zprávy zaslaného prostřednictvím služby MSMQ a korelační pomocí [.NET kontextová výměna](https://go.microsoft.com/fwlink/?LinkID=166059). Zprávy jsou odeslány pomocí <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.Receive> zasílání zpráv aktivity. Kontextová výměna .NET se používá k určení adresa zpětného volání pro odeslané zprávy. Obě služby jsou hostované pomocí služby aktivační procesů Windows (WAS) a jsou nakonfigurované tak, aby stálost instance služby.  
  
 První služby (Service1.xamlx) odešle požadavek službě odeslat (Service2.xamlx) nějakou práci. Po dokončení práce Service2.xamlx oznámení odešle zpět do Service1.xamlx k označení, že práce byla dokončena. Konzolová aplikace pracovního postupu nastaví fronty, které služby naslouchají na a odesílá počáteční zpráva spuštění k aktivaci Service1.xamlx. Jakmile Service1.xamlx obdrží oznámení z Service2.xamlx dokončení požadované pracovní, Service1.xamlx uloží výsledek do souboru XML. Při čekání na zpětné volání zprávy, Service1.xamlx nevyřeší jeho stav instance pomocí výchozího <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior>. Service2.xamlx udržuje svůj stav instance jako součást dokončení práce požadoval Service1.xamlx.  
  
 Ke konfiguraci služby na používání .NET kontextová výměna přes služby MSMQ, obě služby jsou nakonfigurovány pro použití vlastní vazby, který se skládá z <xref:System.ServiceModel.Channels.ContextBindingElement> a <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>. Adresa zpětného volání je zadán s <xref:System.ServiceModel.Channels.ContextBindingElement> a je součástí hlavičku kontextu zpětného volání s všechny zprávy odeslané prostřednictvím vlastní vazby. Následující příklad kódu definuje vlastní vazby.  
  
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
>  Vazba použitá v tomto příkladu není zabezpečený. Při nasazení vaší aplikace byste měli nakonfigurovat vaše vazby na základě požadavků zabezpečení vaší aplikace.  
  
> [!NOTE]
>  Fronty používané v tomto příkladu nejsou transakční. Příklad, který ukazuje, jak nastavit výměny zpráv WCF pomocí fronty transakcí, najdete v článku [aktivace služby MSMQ](../../../../docs/framework/wcf/samples/msmq-activation.md) vzorku.  
  
 Zpráva odeslaná Service1.xamlx Service2.xamlx přijde, že koncový bod klienta nakonfigurovanou adresu Service2.xamlx a vlastní vazby pomocí dříve definovali. Zpětné volání z Service2.xamlx Service1.xamlx se odešle pomocí koncový bod klienta s žádnou explicitně nakonfigurovanou adresu, protože adresa je převzata z kontextu zpětného volání odesílaných Service1.xamlx. Následující příklad kódu definuje koncové body klienta.  
  
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
  
 Následující příklad kódu zveřejňuje koncové body, které používá tuto vlastní vazbu tak, že změníte výchozí mapování protokolů pro základní adresy net.msmq používat tento vlastní vazby.  
  
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
  
 Následující příklad kódu povolí trvalost pro obě služby tak, že přidáte <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> chování služby a zadávání připojovacího řetězce databáze trvalosti.  
  
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
  
2.  Internetová informační služba -> Kompatibilita správy služby IIS 6.0 -> Konfigurace kompatibility metabáze služby IIS a služby IIS 6.0.  
  
3.  Webová služba -> vývoj aplikace ASP.NET-funkce >.  
  
4.  Server Microsoft zpráv fronty (MSMQ).  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Nastavení databáze trvalosti a složka výsledků.  
  
    1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
    2.  Přejděte do složky pro tuto ukázku a spustit Setup.cmd.  
  
2.  Nastavte virtuální aplikace.  
  
    1.  Z [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku, spuštěním následujícího příkazu registrace technologie ASP.NET.  
  
        ```  
        aspnet_regiis -i  
        ```  
  
    2.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] s oprávněními správce kliknutím pravým tlačítkem myši [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a vyberete **spustit jako správce**.  
  
    3.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor DurableDuplex.sln.  
  
3.  Nastavení služby front.  
  
    1.  Pokud chcete spustit klienta DurableDuplex, stisknutím klávesy F5.  
  
    2.  Otevřít **Správa počítače** konzoly spuštěním `Compmgmt.msc` z příkazového řádku.  
  
    3.  Rozbalte **služby a aplikace**, **služby Řízení front zpráv**. **Soukromé fronty**.  
  
    4.  Klikněte pravým tlačítkem na durableduplex/service1.xamlx a durableduplex/service2.xamlx front a vyberte **vlastnosti**.  
  
    5.  Vyberte **zabezpečení** kartu a povolit **přijímat zprávy všem**, **prohlížet zprávy** a **poslat zprávu** oprávnění pro oba front.  
  
    6.  Otevřete Správce Internetové informační služby (IIS).  
  
    7.  Přejděte do **Server**, **lokality**, **výchozí webová stránka**, **privátní**, **trvalý duplexní** a vyberte **Pokročilé možnosti**.  
  
    8.  Změnit **povolené protokoly** k **http,net.msmq**.  
  
4.  Spusťte ukázku.  
  
    1.  Přejděte do http://localhost/private/durableduplex/service1.xamlx a http://localhost/private/durableduplex/service2.xamlx zajistit, že obě služby jsou spuštěny.  
  
    2.  Stisknutím klávesy F5 spusťte DurableDuplexClient.  
  
         Po dokončení výměnu zpráv trvalý duplexní result.xml soubor se uloží do složky C:\Inbox a obsahuje výsledek výměně zpráv.  
  
#### <a name="to-cleanup-optional"></a>Vyčistit (volitelné)  
  
1.  Spusťte Cleanup.cmd.  
  
    1.  Otevřít [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] příkazového řádku.  
  
    2.  Přejděte do složky pro tuto ukázku a spusťte Cleanup.cmd.  
  
2.  Odeberte virtuální aplikace pro služby.  
  
    1.  Otevřete Správce Internetové informační služby (IIS), že spustíte `Inetmgr.exe` z příkazového řádku.  
  
    2.  Přejděte na výchozí web a odebrat **privátní** virtuální adresář.  
  
3.  Odeberte nastavení pro tuto ukázku fronty.  
  
    1.  Otevřete konzolu pro správu počítače spuštěním `Compmgmt.msc` z příkazového řádku.  
  
    2.  Rozbalte **služby a aplikace**, **služby Řízení front zpráv**, **soukromé fronty**.  
  
    3.  Odstraňte durableduplex/service1.xamlx a durableduplex/service2.xamlx fronty.  
  
4.  Odeberte adresář C:\Inbox.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\DurableDuplex`