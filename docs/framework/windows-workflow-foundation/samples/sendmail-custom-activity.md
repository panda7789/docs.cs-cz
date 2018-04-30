---
title: SendMail vlastní aktivity
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 46038466233e7039229890b15b0ad6ca9d1a717f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="sendmail-custom-activity"></a>SendMail vlastní aktivity
Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která je odvozena od <xref:System.Activities.AsyncCodeActivity> k odesílání pošty přes protokol SMTP pro použití v rámci aplikace pracovního postupu. Vlastní aktivita používá možnosti <xref:System.Net.Mail.SmtpClient> asynchronně odesílat e-mailu a odesílat e-maily s ověřováním. Poskytuje také některé funkce koncového uživatele jako testování režim tokenu nahrazení, soubor šablony a otestovat rozevírací cestu.  
  
 V následující tabulce jsou argumenty `SendMail` aktivity.  
  
|Název|Typ|Popis|  
|-|-|-|  
|Hostitel|String|Adresa hostitele serveru SMTP.|  
|port|String|Port služby SMTP na hostiteli.|  
|enableSsl|bool|Určuje, zda <xref:System.Net.Mail.SmtpClient> používá k šifrování připojení Secure Sockets Layer (SSL).|  
|UserName|String|Uživatelské jméno k nastavení pověření pro ověření odesílatel <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnost.|  
|Heslo|String|Heslo k nastavení pověření pro ověření odesílatel <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnost.|  
|Předmět|<xref:System.Activities.InArgument%601>\<řetězec >|Předmět zprávy.|  
|Text|<xref:System.Activities.InArgument%601>\<řetězec >|Text zprávy.|  
|Přílohy|<xref:System.Activities.InArgument%601>\<řetězec >|Kolekce přílohy používají k ukládání dat, které jsou připojené k této e-mailové zprávy.|  
|From|<xref:System.Net.Mail.MailAddress>|Z adresy pro tento e-mailové zprávy.|  
|Chcete-li|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adresu, která obsahuje příjemci tohoto e-mailu.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Adres kolekce, která obsahuje příjemci kopie (kopie) pro tento e-mailové zprávy.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adresu, která obsahuje skrytá kopie (SKRYTÁ) příjemce pro tento e-mailové zprávy.|  
|Tokeny|<xref:System.Activities.InArgument%601>< IDictionary\<řetězec, řetězec >>|Tokenů pro nahrazení v textu. Tato funkce umožňuje uživatelům zadat některé hodnoty v textu, než můžete později nahrazuje tokeny poskytuje používání této vlastnosti.|  
|BodyTemplateFilePath|String|Cesta šablonu pro text. `SendMail` Aktivity zkopíruje obsah tohoto souboru do jeho vlastnost textu.<br /><br /> Šablona může obsahovat tokeny, které jsou nahrazovány obsah vlastnosti tokeny.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Pokud je tato vlastnost nastavena, všechny e-mailů se odesílají na adresu zadanou v ní.<br /><br /> Tato vlastnost je určena pro použití při testování pracovních postupů. Například pokud chcete Ujistěte se, že jsou všechny e-maily odeslány bez odeslání je skutečný příjemcům.|  
|TestDropPath|String|Pokud je tato vlastnost nastavena, všechny e-mailů jsou také uloženy do zadaného souboru.<br /><br /> Tato vlastnost je určena pro použití při testování a ladění pracovních postupů, abyste měli jistotu, že formát a obsah odchozích e-mailů, je vhodné.|  
  
## <a name="solution-contents"></a>Obsah řešení  
 Řešení obsahuje dva projekty.  
  
|Projekt|Popis|Důležité soubory|  
|-------------|-----------------|---------------------|  
|SendMail|SendMail aktivity|1.  SendMail.cs: implementace pro hlavní aktivitu<br />2.  SendMailDesigner.xaml a SendMailDesigner.xaml.cs: návrháře SendMail aktivity<br />3.  MailTemplateBody.htm: Šablona e-mailu mají být odeslány.|  
|SendMailTestClient|Klient k testování SendMail aktivity.  Tento projekt ukazuje dva způsoby vyvolání aktivity SendMail: deklarativně a programově.|1.  Sequence1.XAML: pracovní postup, který vyvolá SendMail aktivity.<br />2.  Program.cs: vyvolá Sequence1 a vytvoří také prostřednictvím kódu programu, používá SendMail pracovního postupu.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Další konfigurace SendMail aktivity  
 I když není uvedeno v ukázce, uživatelé mohou provádět konfiguraci přidání SendMail aktivity. V následujících třech částech ukazují, jak to provést.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>E-mailu pomocí tokenů specifikovat v textu  
 Tento fragment kódu ukazuje, jak můžete odeslat e-mailu pomocí tokenů v textu. Všimněte si, jak jsou uvedeny tokenů v vlastnosti body. Hodnoty pro tyto tokeny jsou k dispozici pro vlastnost tokeny.  
  
```html  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a>E-mailu pomocí šablony  
 Tento fragment kódu ukazuje, jak k odesílání e-mailu pomocí šablony tokeny v textu. Všimněte si, že při nastavení `BodyTemplateFilePath` vlastnost není třeba zadat hodnotu pro vlastnost textu (obsah souboru šablony se zkopírují na text).  
  
```  
new SendMail  
{    
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",   
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a>Odesílání e-mailů v režimu testování  
 Tento fragment kódu ukazuje, jak nastavit dva testování vlastnosti: nastavením `TestMailTo` na všechny zprávy se budou odesílat do john.doe@contoso.con (bez ohledu na hodnoty Komu, skrytá kopie). Nastavením TestDropPath se taky zaznamená všechny odchozí e-mailů v zadané cestě. Tyto vlastnosti můžete nastavit samostatně (nesouvisí).  
  
```  
new SendMail  
{    
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a>Pokyny k instalaci  
 Je vyžadován pro tato ukázka přístup k serveru SMTP.  
  
 Další informace o nastavení serveru SMTP v následujících tématech.  
  
-   [Webu Microsoft Technet](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [Konfigurace služby SMTP (IIS 6.0)](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [Služba IIS 7.0: Konfigurace SMTP E-Mail](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [Jak nainstalovat službu SMTP](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 SMTP emulátorů třetích stran jsou k dispozici ke stažení.  
  
##### <a name="to-run-this-sample"></a>Chcete tuto ukázku spustit  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení SendMail.sln.  
  
2.  Ujistěte se, zda máte přístup k platný název serveru SMTP. Najdete pokyny k instalaci.  
  
3.  Konfigurace programu s touto adresou serveru a od a do e-mailové adresy.  
  
     Pokud chcete tuto ukázku spustit správně, musíte nakonfigurovat hodnotu od a do e-mailové adresy a adresy serveru SMTP v souboru Program.cs a Sequence.xaml. Budete muset změnit adresu v obou umístěních, protože program odešle mail dvěma různými způsoby  
  
4.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
5.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`