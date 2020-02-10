---
title: Vlastní aktivita SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 90b3192d931b216345b50ba49465455427e43a64
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77094602"
---
# <a name="sendmail-custom-activity"></a>Vlastní aktivita SendMail
V této ukázce se dozvíte, jak vytvořit vlastní aktivitu, která se odvozuje z <xref:System.Activities.AsyncCodeActivity> k odeslání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu. Vlastní aktivita využívá možnosti <xref:System.Net.Mail.SmtpClient> k asynchronnímu posílání e-mailů a k odesílání e-mailů s ověřováním. Poskytuje také některé funkce koncového uživatele, jako je režim testu, nahrazení tokenu, šablony souborů a cesta pro vyřazení testu.  
  
 Následující tabulka popisuje argumenty aktivity `SendMail`.  
  
|Název|Typ|Popis|  
|-|-|-|  
|Hostitel|Řetězec|Adresa hostitele serveru SMTP.|  
|Port|Řetězec|Port služby SMTP v hostiteli.|  
|EnableSsl|bool|Určuje, jestli <xref:System.Net.Mail.SmtpClient> k šifrování připojení používá SSL (Secure Sockets Layer) (SSL).|  
|UserName|Řetězec|Uživatelské jméno pro nastavení přihlašovacích údajů pro ověření vlastnosti odesílatele <xref:System.Net.Mail.SmtpClient.Credentials%2A>.|  
|Heslo|Řetězec|Heslo pro nastavení přihlašovacích údajů pro ověření vlastnosti odesílatele <xref:System.Net.Mail.SmtpClient.Credentials%2A>.|  
|Subjekt|řetězec \<<xref:System.Activities.InArgument%601>>|Předmět zprávy|  
|Tělo|řetězec \<<xref:System.Activities.InArgument%601>>|Text zprávy|  
|Přílohy|řetězec \<<xref:System.Activities.InArgument%601>>|Kolekce příloh používaná k ukládání dat připojených k této e-mailové zprávě|  
|Z|<xref:System.Net.Mail.MailAddress>|Z adresy pro tuto e-mailovou zprávu.|  
|Akce|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje příjemce této e-mailové zprávy.|  
|CC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje příjemce kopie (CC) pro tuto e-mailovou zprávu.|  
|BCC|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|Kolekce adres, která obsahuje příjemce skryté kopie (BCC) pro tuto e-mailovou zprávu.|  
|Tokeny|<xref:System.Activities.InArgument%601>< IDictionary\<String, String > >|Tokeny, které mají být nahrazeny v těle. Tato funkce umožňuje uživatelům zadat v těle některé hodnoty, než je lze později nahradit tokeny poskytnutými pomocí této vlastnosti.|  
|BodyTemplateFilePath|Řetězec|Cesta k šabloně pro tělo Aktivita `SendMail` kopíruje obsah tohoto souboru do vlastnosti body.<br /><br /> Šablona může obsahovat tokeny, které jsou nahrazeny obsahem vlastnosti tokeny.|  
|TestMailTo|<xref:System.Net.Mail.MailAddress>|Když je tato vlastnost nastavená, všechny e-maily se odešlou na adresu uvedenou v ní.<br /><br /> Tato vlastnost je určena pro použití při testování pracovních postupů. Například pokud chcete zajistit, aby byly všechny e-maily odeslány bez jejich odeslání skutečným příjemcům.|  
|TestDropPath|Řetězec|Když je tato vlastnost nastavená, všechny e-maily se uloží i do zadaného souboru.<br /><br /> Tato vlastnost je určena k použití při testování nebo ladění pracovních postupů, abyste se ujistili, že formát a obsah odchozích e-mailů je vhodný.|  
  
## <a name="solution-contents"></a>Obsah řešení  
 Řešení obsahuje dva projekty.  
  
|Project|Popis|Důležité soubory|  
|-------------|-----------------|---------------------|  
|SendMail|Aktivita SendMail|1. SendMail.cs: implementace hlavní aktivity<br />2. SendMailDesigner. XAML a SendMailDesigner.xaml.cs: Návrhář pro aktivitu SendMail<br />3. MailTemplateBody. htm: Šablona pro odeslání e-mailu.|  
|SendMailTestClient|Klient pro otestování aktivity SendMail  Tento projekt znázorňuje dva způsoby volání aktivity SendMail: deklarativně a programově.|1. Sequence1. XAML: pracovní postup, který vyvolá aktivitu SendMail.<br />2. Program.cs: vyvolá Sequence1 a také vytvoří pracovní postup programově, který používá SendMail.|  
  
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
 Tento fragment kódu ukazuje, jak odeslat e-mail pomocí tokenů šablony v těle. Všimněte si, že při nastavování vlastnosti `BodyTemplateFilePath` nepotřebujeme zadat hodnotu vlastnosti tělo (obsah souboru šablony se zkopíruje do těla).  
  
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
 Tento fragment kódu ukazuje, jak nastavit vlastnosti dvou testů: nastavením `TestMailTo` na všechny zprávy bude odesláno do `john.doe@contoso.con` (bez ohledu na hodnoty do, kopie, Skrytá kopie). Nastavením TestDropPath všech odchozích e-mailů se také zaznamená v zadané cestě. Tyto vlastnosti lze nastavit nezávisle (nejsou v relaci).  
  
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
  
- [Konfigurace služby SMTP (IIS 6,0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))  
  
- [IIS 7,0: Konfigurace e-mailu SMTP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))  
  
- [Jak nainstalovat službu SMTP](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))  
  
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
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
