---
title: Vlastní aktivita SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 5797620c4938d7dcffb1f506b682141336b21eab
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988985"
---
# <a name="sendmail-custom-activity"></a>Vlastní aktivita SendMail
V této ukázce se dozvíte, jak vytvořit vlastní aktivitu, která <xref:System.Activities.AsyncCodeActivity> se odvozuje z k odeslání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu. Vlastní aktivita využívá možnosti <xref:System.Net.Mail.SmtpClient> k asynchronnímu posílání e-mailů a k odesílání e-mailů s ověřováním. Poskytuje také některé funkce koncového uživatele, jako je režim testu, nahrazení tokenu, šablony souborů a cesta pro vyřazení testu.  
  
 Následující tabulka popisuje argumenty pro `SendMail` aktivitu.  
  
|Name|Typ|Popis|  
|-|-|-|  
|Hostitel|String|Adresa hostitele serveru SMTP.|  
|Port|String|Port služby SMTP v hostiteli.|  
|enableSsl|bool|Určuje, jestli <xref:System.Net.Mail.SmtpClient> k šifrování připojení používá SSL (Secure Sockets Layer) (SSL).|  
|UserName|String|Uživatelské jméno pro nastavení přihlašovacích údajů pro ověření vlastnosti <xref:System.Net.Mail.SmtpClient.Credentials%2A> Sender.|  
|Heslo|String|Heslo pro nastavení přihlašovacích údajů pro ověření vlastnosti Sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> .|  
|Subject|<xref:System.Activities.InArgument%601>\<> řetězců|Předmět zprávy|  
|Tělo|<xref:System.Activities.InArgument%601>\<> řetězců|Text zprávy|  
|Přílohy|<xref:System.Activities.InArgument%601>\<> řetězců|Kolekce příloh používaná k ukládání dat připojených k této e-mailové zprávě|  
|From|<xref:System.Net.Mail.MailAddress>|Z adresy pro tuto e-mailovou zprávu.|  
|Chcete-li|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje příjemce této e-mailové zprávy.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje příjemce kopie (CC) pro tuto e-mailovou zprávu.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje příjemce skryté kopie (BCC) pro tuto e-mailovou zprávu.|  
|Tokeny|<xref:System.Activities.InArgument%601>< řetězec\<IDictionary, > řetězce >|Tokeny, které mají být nahrazeny v těle. Tato funkce umožňuje uživatelům zadat v těle některé hodnoty, než je lze později nahradit tokeny poskytnutými pomocí této vlastnosti.|  
|BodyTemplateFilePath|String|Cesta k šabloně pro tělo `SendMail` Aktivita zkopíruje obsah tohoto souboru do vlastnosti body.<br /><br /> Šablona může obsahovat tokeny, které jsou nahrazeny obsahem vlastnosti tokeny.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Když je tato vlastnost nastavená, všechny e-maily se odešlou na adresu uvedenou v ní.<br /><br /> Tato vlastnost je určena pro použití při testování pracovních postupů. Například pokud chcete zajistit, aby byly všechny e-maily odeslány bez jejich odeslání skutečným příjemcům.|  
|TestDropPath|String|Když je tato vlastnost nastavená, všechny e-maily se uloží i do zadaného souboru.<br /><br /> Tato vlastnost je určena k použití při testování nebo ladění pracovních postupů, abyste se ujistili, že formát a obsah odchozích e-mailů je vhodný.|  
  
## <a name="solution-contents"></a>Obsah řešení  
 Řešení obsahuje dva projekty.  
  
|Project|Popis|Důležité soubory|  
|-------------|-----------------|---------------------|  
|SendMail|Aktivita SendMail|1.  SendMail.cs: implementace hlavní aktivity<br />2.  SendMailDesigner. XAML a SendMailDesigner.xaml.cs: Návrhář pro aktivitu SendMail<br />3.  MailTemplateBody. htm: Šablona pro odeslání e-mailu.|  
|SendMailTestClient|Klient pro otestování aktivity SendMail  Tento projekt znázorňuje dva způsoby volání aktivity SendMail: deklarativně a programově.|1.  Sequence1. XAML: pracovní postup, který vyvolá aktivitu SendMail.<br />2.  Program.cs: vyvolá Sequence1 a také vytvoří pracovní postup programově, který používá SendMail.|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a>Další konfigurace aktivity SendMail  
 I když v ukázce není zobrazený, můžou uživatelé provádět i konfiguraci aktivity SendMail. Další tři části ukazují, jak to uděláte.  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a>Odeslání e-mailu pomocí tokenů zadaných v těle  
 Tento fragment kódu ukazuje, jak můžete odeslat e-mail s tokeny v těle. Všimněte si, jak jsou tokeny k dispozici ve vlastnosti body. Hodnoty pro tyto tokeny jsou k dispozici pro vlastnost tokeny.  
  
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
 Tento fragment kódu ukazuje, jak odeslat e-mail pomocí tokenů šablony v těle. Všimněte si, že při `BodyTemplateFilePath` nastavování vlastnosti není nutné zadávat hodnotu vlastnosti tělo (obsah souboru šablony bude zkopírován do těla).  
  
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
 Tento fragment kódu ukazuje, jak nastavit vlastnosti dvou testů: `TestMailTo` nastavením na všechny zprávy se `john.doe@contoso.con` pošle (bez ohledu na hodnoty do, kopie, Skrytá kopie). Nastavením TestDropPath všech odchozích e-mailů se také zaznamená v zadané cestě. Tyto vlastnosti lze nastavit nezávisle (nejsou v relaci).  
  
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
  
 Další informace o nastavení serveru SMTP najdete na následujících odkazech.  
  
- [Microsoft Technet](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [Konfigurace služby SMTP (IIS 6,0)](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [IIS 7.0: Konfigurace e-mailu SMTP](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [Jak nainstalovat službu SMTP](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 Emulátory SMTP poskytované třetími stranami jsou k dispozici ke stažení.  
  
##### <a name="to-run-this-sample"></a>Spuštění této ukázky  
  
1. Pomocí sady Visual Studio 2010 otevřete soubor řešení SendMail. sln.  
  
2. Ujistěte se, že máte přístup k platnému serveru SMTP. Projděte si pokyny pro nastavení.  
  
3. Nakonfigurujte program s adresou serveru, a to od a po e-mailové adresy.  
  
     Pro správné spuštění této ukázky může být nutné nakonfigurovat hodnotu z a na e-mailové adresy a adresu serveru SMTP v Program.cs a Sequence. XAML. Tuto adresu budete muset změnit v obou umístěních, protože program odesílá e-maily dvěma různými způsoby.  
  
4. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
5. Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
