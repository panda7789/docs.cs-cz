---
title: Vlastní aktivita SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: e7cc64e68c3d78b9ee7ec813700e96a52c239141
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182773"
---
# <a name="sendmail-custom-activity"></a>Vlastní aktivita SendMail
Tato ukázka ukazuje, jak vytvořit vlastní <xref:System.Activities.AsyncCodeActivity> aktivitu, která je odvozena od odesílání pošty pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu. Vlastní aktivita využívá <xref:System.Net.Mail.SmtpClient> možnosti odesílání e-mailu asynchronně a odesílání pošty s ověřováním. Poskytuje také některé funkce koncového uživatele, jako je testovací režim, nahrazení tokenu, šablony souborů a cesta k přetažení testu.  
  
 V následující tabulce jsou podrobně `SendMail` uvedeny argumenty pro aktivitu.  
  
|Name (Název)|Typ|Popis|  
|-|-|-|  
|Hostitel|Řetězec|Adresa hostitele serveru SMTP.|  
|Port|Řetězec|Port služby SMTP v hostiteli.|  
|EnableSsl|bool|Určuje, <xref:System.Net.Mail.SmtpClient> zda k šifrování připojení používá ssl (Secure Sockets Layer).|  
|UserName|Řetězec|Uživatelské jméno pro nastavení pověření k ověření <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnosti odesílatele.|  
|Heslo|Řetězec|Heslo pro nastavení pověření k ověření <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnosti odesílatele.|  
|Subjekt|<xref:System.Activities.InArgument%601>\<řetězec>|Předmět zprávy.|  
|Tělo|<xref:System.Activities.InArgument%601>\<řetězec>|Text zprávy.|  
|Přílohy|<xref:System.Activities.InArgument%601>\<řetězec>|Kolekce příloh používaná k ukládání dat připojených k této e-mailové zprávě.|  
|From|<xref:System.Net.Mail.MailAddress>|Z adresy pro tuto e-mailovou zprávu.|  
|Akce|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje příjemce této e-mailové zprávy.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje příjemce kopie (CC) pro tuto e-mailovou zprávu.|  
|Skrytá|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje skryté uhlíkové kopie (SKRYTÁ) příjemci pro tuto e-mailovou zprávu.|  
|Tokeny|<xref:System.Activities.InArgument%601><Řetězec\<IDictionary, řetězec>>|Tokeny nahradit v těle. Tato funkce umožňuje uživatelům zadat některé hodnoty v těle, než může být nahrazen později tokeny poskytované pomocí této vlastnosti.|  
|Cesta BodyTemplateFilePath|Řetězec|Cesta šablony pro tělo. Aktivita `SendMail` zkopíruje obsah tohoto souboru do jeho vlastnosti těla.<br /><br /> Šablona může obsahovat tokeny, které jsou nahrazeny obsahem vlastnosti tokeny.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Pokud je tato vlastnost nastavena, všechny e-maily jsou odesílány na adresu uvedenou v něm.<br /><br /> Tato vlastnost je určena pro použití při testování pracovních postupů. Například pokud chcete zajistit, aby všechny e-maily byly odeslány bez jejich odeslání skutečným příjemcům.|  
|TestDropPath|Řetězec|Pokud je tato vlastnost nastavena, všechny e-maily jsou také uloženy v zadaném souboru.<br /><br /> Tato vlastnost je určena pro použití při testování nebo ladění pracovních postupů, abyste se ujistili, že formát a obsah odchozích e-mailů je vhodný.|  
  
## <a name="solution-contents"></a>Obsah roztoku  
 Řešení obsahuje dva projekty.  
  
|Project|Popis|Důležité soubory|  
|-------------|-----------------|---------------------|  
|Sendmail|Aktivita SendMail|1. SendMail.cs: provádění hlavní činnosti<br />2. SendMailDesigner.xaml a SendMailDesigner.xaml.cs: návrhář pro sendmail aktivitu<br />3. MailTemplateBody.htm: šablona pro e-mail, který má být odeslán.|  
|OdeslatklientMailTest|Klient otestovat SendMail aktivitu.  Tento projekt ukazuje dva způsoby vyvolání SendMail aktivity: deklarativně a programově.|1. Sequence1.xaml: pracovní postup, který vyvolá sendmail aktivitu.<br />2. Program.cs: vyvolá Sequence1 a také vytvoří programově pracovní postup, který používá SendMail.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Další konfigurace aktivity SendMail  
 Ačkoli nejsou zobrazeny v ukázce, uživatelé mohou provádět přidání konfigurace SendMail aktivity. Následující tři části ukazují, jak se to dělá.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Odeslání e-mailu pomocí tokenů určených v těle  
 Tento fragment kódu ukazuje, jak můžete odesílat e-maily s tokeny v těle. Všimněte si, jak tokeny jsou k dispozici v těle vlastnosti. Hodnoty pro tyto tokeny jsou k dispozici tokeny vlastnost.  
  
```csharp  
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
  
### <a name="sending-an-email-using-a-template"></a>Odeslání e-mailu pomocí šablony  
 Tento úryvek ukazuje, jak odeslat e-mail pomocí tokenů šablony v těle. Všimněte si, `BodyTemplateFilePath` že při nastavování vlastnosti nemusíme poskytovat hodnotu vlastnosti Body (obsah souboru šablony bude zkopírován do těla).  
  
```csharp  
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
  
### <a name="sending-mails-in-testing-mode"></a>Odesílání e-mailů v testovacím režimu  
 Tento fragment kódu ukazuje, jak nastavit dvě vlastnosti `TestMailTo` testování: nastavením `john.doe@contoso.con` na všechny zprávy budou odeslány do (bez ohledu na hodnoty To, Kopie, Skrytá). Nastavením TestDropPath všechny odchozí e-maily budou také zaznamenány v poskytnuté cestě. Tyto vlastnosti lze nastavit nezávisle (nesouvisí).  
  
```csharp  
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
 Pro tuto ukázku je vyžadován přístup k serveru SMTP.  
  
 Další informace o nastavení serveru SMTP naleznete v následujících odkazech.  
  
- [Konfigurace služby SMTP (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))  
  
- [IIS 7.0: Konfigurace e-mailu SMTP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))  
  
- [Jak nainstalovat službu SMTP](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))  
  
 Emulátory SMTP poskytované třetími stranami jsou k dispozici ke stažení.  
  
##### <a name="to-run-this-sample"></a>Spuštění této ukázky  
  
1. Pomocí sady Visual Studio 2010 otevřete soubor řešení SendMail.sln.  
  
2. Ujistěte se, že máte přístup k platnému serveru SMTP. Podívejte se na pokyny k nastavení.  
  
3. Nakonfigurujte program pomocí adresy serveru a e-mailových adres Od a Do.  
  
     Chcete-li správně spustit tuto ukázku, bude pravděpodobně nutné nakonfigurovat hodnotu e-mailových adres From a To a adresu serveru SMTP v Program.cs a v Sequence.xaml. Budete muset změnit adresu v obou místech, protože program odesílá poštu dvěma různými způsoby  
  
4. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.  
  
5. Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
