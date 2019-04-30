---
title: Vlastní aktivita SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 89252098402deee991ea01b8e76082a5f4b8c389
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785941"
---
# <a name="sendmail-custom-activity"></a>Vlastní aktivita SendMail
Tato ukázka předvádí, jak vytvořit vlastní aktivitu, která je odvozena z <xref:System.Activities.AsyncCodeActivity> k odesílání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu. Vlastní aktivita používá možnosti <xref:System.Net.Mail.SmtpClient> asynchronní odeslání e-mailu a odesílání e-mailu s ověřováním. Poskytuje také některé funkce koncových uživatelů, jako je režim, nahrazování tokenů, soubor šablony a testujte cestu pro přetažení.  
  
 Následující tabulka obsahuje podrobnosti o argumenty `SendMail` aktivity.  
  
|Název|Typ|Popis|  
|-|-|-|  
|Hostitel|String|Adresa hostitele serveru SMTP.|  
|Port|String|Port služby SMTP na hostiteli.|  
|enableSsl|bool|Určuje, zda <xref:System.Net.Mail.SmtpClient> vrstvy SSL (Secure Sockets) používá k šifrování připojení.|  
|UserName|String|Uživatelské jméno pro nastavení přihlašovacích údajů pro ověření odesílatel <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnost.|  
|Heslo|String|Heslo k nastavení pověření pro ověření odesílatel <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnost.|  
|Subject|<xref:System.Activities.InArgument%601>\<řetězec >|Předmět zprávy.|  
|Tělo|<xref:System.Activities.InArgument%601>\<řetězec >|Text zprávy.|  
|Přílohy|<xref:System.Activities.InArgument%601>\<řetězec >|Kolekce přílohy sloužící k ukládání dat, které jsou připojené k této e-mailové zprávy.|  
|From|<xref:System.Net.Mail.MailAddress>|Z adresy pro tento e-mailové zprávy.|  
|Chcete-li|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, který obsahuje příjemci tohoto e-mailové zprávy.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Adresa kolekce, která obsahuje příjemci kopie (CC) pro tento e-mailové zprávy.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, který obsahuje příjemci skryté kopie (SKRYTÁ) pro tento e-mailové zprávy.|  
|Tokeny|<xref:System.Activities.InArgument%601>< IDictionary\<řetězec, řetězec >>|Tokeny pro nahrazení v textu. Tato funkce umožňuje uživatelům zadat některé hodnoty v textu, než lze později nahradit tokeny k dispozici pomocí této vlastnosti.|  
|BodyTemplateFilePath|String|Cesta k šabloně pro tělo. `SendMail` Aktivita kopíruje obsah tohoto souboru do jeho vlastnosti body.<br /><br /> Šablona může obsahovat tokeny, které jsou nahrazeny obsah vlastnosti tokeny.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Pokud je tato vlastnost nastavena, všechny e-maily se odesílají na adresu zadanou v ní.<br /><br /> Tato vlastnost je určena pro použití při testování pracovních postupů. Například pokud chcete Ujistěte se, že všechny mailů bez odeslání skutečné příjemcům.|  
|TestDropPath|String|Pokud je tato vlastnost nastavena, všechny e-maily jsou také uloženy ve zadaného souboru.<br /><br /> Tato vlastnost je určena pro použití při testování nebo ladění pracovních postupů, abyste měli jistotu, že je příslušný formát a obsah odchozích e-mailů.|  
  
## <a name="solution-contents"></a>Obsah řešení  
 Řešení obsahuje dva projekty.  
  
|Project|Popis|Důležitých souborů|  
|-------------|-----------------|---------------------|  
|SendMail|Aktivita SendMail|1.  SendMail.cs: implementace pro hlavní aktivitu<br />2.  SendMailDesigner.xaml a SendMailDesigner.xaml.cs: návrháře pro aktivita SendMail<br />3.  MailTemplateBody.htm: Šablona e-mailu k odeslání.|  
|SendMailTestClient|Testovací aktivita SendMail klienta.  Tento projekt ukazuje dva způsoby volání aktivita SendMail: deklarativně a prostřednictvím kódu programu.|1.  Sequence1.XAML: pracovní postup, který volá aktivita SendMail.<br />2.  Soubor program.cs: vyvolá Sequence1 a také vytvoří pracovní postup prostřednictvím kódu programu, který používá SendMail.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Další konfigurace aktivita SendMail  
 I když není zobrazený ve vzorku, uživatelé mohou provádět přidání konfigurace aktivita SendMail. V následujících třech částech ukazují, jak to lze provést.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Odesílání e-mailu pomocí tokenů zadaná v těle  
 Tento fragment kódu ukazuje, jak můžete poslat e-mailu s tokeny v textu. Všimněte si, jak jsou k dispozici tokeny ve vlastnosti tělo. Hodnoty pro tyto tokeny jsou k dispozici na vlastnost tokeny.  
  
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
  
### <a name="sending-an-email-using-a-template"></a>Odesílání e-mailu pomocí šablony  
 Tento fragment kódu ukazuje, jak odesílat e-maily pomocí šablony tokeny v textu. Všimněte si, že při nastavení `BodyTemplateFilePath` vlastnost nemusíme poskytovat hodnotu pro vlastnost text (obsah souboru šablony se zkopíruje do textu).  
  
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
  
### <a name="sending-mails-in-testing-mode"></a>Odesílání e-mailů při testování režimu  
 Tento fragment kódu ukazuje, jak nastavit vlastnosti testování dvě: nastavením `TestMailTo` pro všechny zprávy se odešlou do `john.doe@contoso.con` (bez ohledu na hodnoty Komu, kopie, skrytá). Nastavením TestDropPath se také zaznamená všechny odchozí e-mailů v zadané cestě. Tyto vlastnosti můžete nastavit samostatně (nesouvisí).  
  
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
 Přístup k serveru SMTP je vyžadován pro tuto ukázku.  
  
 Další informace o nastavení serveru SMTP najdete na následujících odkazech.  
  
- [Microsoft Technet](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [Konfigurace SMTP služby (IIS 6.0)](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [IIS 7.0: Konfigurace e-mailu SMTP](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [Jak nainstalovat službu SMTP](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Emulátory SMTP třetích stran jsou k dispozici ke stažení.  
  
##### <a name="to-run-this-sample"></a>Tuto ukázku spustit  
  
1. Pomocí sady Visual Studio 2010, otevřete soubor řešení SendMail.sln.  
  
2. Ujistěte se, že máte přístup k SMTP serveru platný. Zobrazit pokyny k instalaci.  
  
3. Konfigurace programu s adresu serveru a od a do e-mailové adresy.  
  
     Pro správné spuštění této ukázky, budete muset nakonfigurovat hodnotu od a do e-mailové adresy a adresu serveru SMTP v souboru Program.cs a Sequence.xaml. Budete muset změnit adresu i v cloudu, protože program odešle e-mailu dvěma různými způsoby  
  
4. Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
5. Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`