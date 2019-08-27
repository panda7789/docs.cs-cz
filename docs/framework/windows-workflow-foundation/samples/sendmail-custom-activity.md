---
title: Vlastní aktivita SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: 9325817a24fee3ba04c2c305ebfdfbc6ff6da1bd
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038116"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="0c794-102">Vlastní aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="0c794-102">SendMail Custom Activity</span></span>
<span data-ttu-id="0c794-103">V této ukázce se dozvíte, jak vytvořit vlastní aktivitu, která <xref:System.Activities.AsyncCodeActivity> se odvozuje z k odeslání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="0c794-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="0c794-104">Vlastní aktivita využívá možnosti <xref:System.Net.Mail.SmtpClient> k asynchronnímu posílání e-mailů a k odesílání e-mailů s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="0c794-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="0c794-105">Poskytuje také některé funkce koncového uživatele, jako je režim testu, nahrazení tokenu, šablony souborů a cesta pro vyřazení testu.</span><span class="sxs-lookup"><span data-stu-id="0c794-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="0c794-106">Následující tabulka popisuje argumenty pro `SendMail` aktivitu.</span><span class="sxs-lookup"><span data-stu-id="0c794-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="0c794-107">Name</span><span class="sxs-lookup"><span data-stu-id="0c794-107">Name</span></span>|<span data-ttu-id="0c794-108">Typ</span><span class="sxs-lookup"><span data-stu-id="0c794-108">Type</span></span>|<span data-ttu-id="0c794-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0c794-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="0c794-110">Hostitel</span><span class="sxs-lookup"><span data-stu-id="0c794-110">Host</span></span>|<span data-ttu-id="0c794-111">String</span><span class="sxs-lookup"><span data-stu-id="0c794-111">String</span></span>|<span data-ttu-id="0c794-112">Adresa hostitele serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="0c794-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="0c794-113">Port</span><span class="sxs-lookup"><span data-stu-id="0c794-113">Port</span></span>|<span data-ttu-id="0c794-114">String</span><span class="sxs-lookup"><span data-stu-id="0c794-114">String</span></span>|<span data-ttu-id="0c794-115">Port služby SMTP v hostiteli.</span><span class="sxs-lookup"><span data-stu-id="0c794-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="0c794-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="0c794-116">EnableSsl</span></span>|<span data-ttu-id="0c794-117">bool</span><span class="sxs-lookup"><span data-stu-id="0c794-117">bool</span></span>|<span data-ttu-id="0c794-118">Určuje, jestli <xref:System.Net.Mail.SmtpClient> k šifrování připojení používá SSL (Secure Sockets Layer) (SSL).</span><span class="sxs-lookup"><span data-stu-id="0c794-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="0c794-119">UserName</span><span class="sxs-lookup"><span data-stu-id="0c794-119">UserName</span></span>|<span data-ttu-id="0c794-120">String</span><span class="sxs-lookup"><span data-stu-id="0c794-120">String</span></span>|<span data-ttu-id="0c794-121">Uživatelské jméno pro nastavení přihlašovacích údajů pro ověření vlastnosti <xref:System.Net.Mail.SmtpClient.Credentials%2A> Sender.</span><span class="sxs-lookup"><span data-stu-id="0c794-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="0c794-122">Heslo</span><span class="sxs-lookup"><span data-stu-id="0c794-122">Password</span></span>|<span data-ttu-id="0c794-123">String</span><span class="sxs-lookup"><span data-stu-id="0c794-123">String</span></span>|<span data-ttu-id="0c794-124">Heslo pro nastavení přihlašovacích údajů pro ověření vlastnosti Sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> .</span><span class="sxs-lookup"><span data-stu-id="0c794-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="0c794-125">Subject</span><span class="sxs-lookup"><span data-stu-id="0c794-125">Subject</span></span>|<span data-ttu-id="0c794-126"><xref:System.Activities.InArgument%601>\<> řetězců</span><span class="sxs-lookup"><span data-stu-id="0c794-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="0c794-127">Předmět zprávy</span><span class="sxs-lookup"><span data-stu-id="0c794-127">Subject of the message.</span></span>|  
|<span data-ttu-id="0c794-128">Tělo</span><span class="sxs-lookup"><span data-stu-id="0c794-128">Body</span></span>|<span data-ttu-id="0c794-129"><xref:System.Activities.InArgument%601>\<> řetězců</span><span class="sxs-lookup"><span data-stu-id="0c794-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="0c794-130">Text zprávy</span><span class="sxs-lookup"><span data-stu-id="0c794-130">Body of the message.</span></span>|  
|<span data-ttu-id="0c794-131">Přílohy</span><span class="sxs-lookup"><span data-stu-id="0c794-131">Attachments</span></span>|<span data-ttu-id="0c794-132"><xref:System.Activities.InArgument%601>\<> řetězců</span><span class="sxs-lookup"><span data-stu-id="0c794-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="0c794-133">Kolekce příloh používaná k ukládání dat připojených k této e-mailové zprávě</span><span class="sxs-lookup"><span data-stu-id="0c794-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="0c794-134">From</span><span class="sxs-lookup"><span data-stu-id="0c794-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="0c794-135">Z adresy pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="0c794-135">From address for this email message.</span></span>|  
|<span data-ttu-id="0c794-136">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="0c794-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="0c794-137">Kolekce adres, která obsahuje příjemce této e-mailové zprávy.</span><span class="sxs-lookup"><span data-stu-id="0c794-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="0c794-138">CC</span><span class="sxs-lookup"><span data-stu-id="0c794-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="0c794-139">Kolekce adres, která obsahuje příjemce kopie (CC) pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="0c794-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="0c794-140">BCC</span><span class="sxs-lookup"><span data-stu-id="0c794-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="0c794-141">Kolekce adres, která obsahuje příjemce skryté kopie (BCC) pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="0c794-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="0c794-142">Tokeny</span><span class="sxs-lookup"><span data-stu-id="0c794-142">Tokens</span></span>|<span data-ttu-id="0c794-143"><xref:System.Activities.InArgument%601>< řetězec\<IDictionary, > řetězce ></span><span class="sxs-lookup"><span data-stu-id="0c794-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="0c794-144">Tokeny, které mají být nahrazeny v těle.</span><span class="sxs-lookup"><span data-stu-id="0c794-144">Tokens to replace in the body.</span></span> <span data-ttu-id="0c794-145">Tato funkce umožňuje uživatelům zadat v těle některé hodnoty, než je lze později nahradit tokeny poskytnutými pomocí této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0c794-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="0c794-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="0c794-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="0c794-147">String</span><span class="sxs-lookup"><span data-stu-id="0c794-147">String</span></span>|<span data-ttu-id="0c794-148">Cesta k šabloně pro tělo</span><span class="sxs-lookup"><span data-stu-id="0c794-148">Path of a template for the body.</span></span> <span data-ttu-id="0c794-149">`SendMail` Aktivita zkopíruje obsah tohoto souboru do vlastnosti body.</span><span class="sxs-lookup"><span data-stu-id="0c794-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="0c794-150">Šablona může obsahovat tokeny, které jsou nahrazeny obsahem vlastnosti tokeny.</span><span class="sxs-lookup"><span data-stu-id="0c794-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="0c794-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="0c794-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="0c794-152">Když je tato vlastnost nastavená, všechny e-maily se odešlou na adresu uvedenou v ní.</span><span class="sxs-lookup"><span data-stu-id="0c794-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="0c794-153">Tato vlastnost je určena pro použití při testování pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="0c794-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="0c794-154">Například pokud chcete zajistit, aby byly všechny e-maily odeslány bez jejich odeslání skutečným příjemcům.</span><span class="sxs-lookup"><span data-stu-id="0c794-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="0c794-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="0c794-155">TestDropPath</span></span>|<span data-ttu-id="0c794-156">String</span><span class="sxs-lookup"><span data-stu-id="0c794-156">String</span></span>|<span data-ttu-id="0c794-157">Když je tato vlastnost nastavená, všechny e-maily se uloží i do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="0c794-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="0c794-158">Tato vlastnost je určena k použití při testování nebo ladění pracovních postupů, abyste se ujistili, že formát a obsah odchozích e-mailů je vhodný.</span><span class="sxs-lookup"><span data-stu-id="0c794-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="0c794-159">Obsah řešení</span><span class="sxs-lookup"><span data-stu-id="0c794-159">Solution Contents</span></span>  
 <span data-ttu-id="0c794-160">Řešení obsahuje dva projekty.</span><span class="sxs-lookup"><span data-stu-id="0c794-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="0c794-161">Project</span><span class="sxs-lookup"><span data-stu-id="0c794-161">Project</span></span>|<span data-ttu-id="0c794-162">Popis</span><span class="sxs-lookup"><span data-stu-id="0c794-162">Description</span></span>|<span data-ttu-id="0c794-163">Důležité soubory</span><span class="sxs-lookup"><span data-stu-id="0c794-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="0c794-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="0c794-164">SendMail</span></span>|<span data-ttu-id="0c794-165">Aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="0c794-165">The SendMail activity</span></span>|<span data-ttu-id="0c794-166">1.  SendMail.cs: implementace hlavní aktivity</span><span class="sxs-lookup"><span data-stu-id="0c794-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="0c794-167">2.  SendMailDesigner. XAML a SendMailDesigner.xaml.cs: Návrhář pro aktivitu SendMail</span><span class="sxs-lookup"><span data-stu-id="0c794-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="0c794-168">3.  MailTemplateBody. htm: Šablona pro odeslání e-mailu.</span><span class="sxs-lookup"><span data-stu-id="0c794-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="0c794-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="0c794-169">SendMailTestClient</span></span>|<span data-ttu-id="0c794-170">Klient pro otestování aktivity SendMail</span><span class="sxs-lookup"><span data-stu-id="0c794-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="0c794-171">Tento projekt znázorňuje dva způsoby volání aktivity SendMail: deklarativně a programově.</span><span class="sxs-lookup"><span data-stu-id="0c794-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="0c794-172">1.  Sequence1. XAML: pracovní postup, který vyvolá aktivitu SendMail.</span><span class="sxs-lookup"><span data-stu-id="0c794-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="0c794-173">2.  Program.cs: vyvolá Sequence1 a také vytvoří pracovní postup programově, který používá SendMail.</span><span class="sxs-lookup"><span data-stu-id="0c794-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="0c794-174">Další konfigurace aktivity SendMail</span><span class="sxs-lookup"><span data-stu-id="0c794-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="0c794-175">I když v ukázce není zobrazený, můžou uživatelé provádět i konfiguraci aktivity SendMail.</span><span class="sxs-lookup"><span data-stu-id="0c794-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="0c794-176">Další tři části ukazují, jak to uděláte.</span><span class="sxs-lookup"><span data-stu-id="0c794-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="0c794-177">Odeslání e-mailu pomocí tokenů zadaných v těle</span><span class="sxs-lookup"><span data-stu-id="0c794-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="0c794-178">Tento fragment kódu ukazuje, jak můžete odeslat e-mail s tokeny v těle.</span><span class="sxs-lookup"><span data-stu-id="0c794-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="0c794-179">Všimněte si, jak jsou tokeny k dispozici ve vlastnosti body.</span><span class="sxs-lookup"><span data-stu-id="0c794-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="0c794-180">Hodnoty pro tyto tokeny jsou k dispozici pro vlastnost tokeny.</span><span class="sxs-lookup"><span data-stu-id="0c794-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="0c794-181">Odeslání e-mailu pomocí šablony</span><span class="sxs-lookup"><span data-stu-id="0c794-181">Sending an email using a template</span></span>  
 <span data-ttu-id="0c794-182">Tento fragment kódu ukazuje, jak odeslat e-mail pomocí tokenů šablony v těle.</span><span class="sxs-lookup"><span data-stu-id="0c794-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="0c794-183">Všimněte si, že při `BodyTemplateFilePath` nastavování vlastnosti není nutné zadávat hodnotu vlastnosti tělo (obsah souboru šablony bude zkopírován do těla).</span><span class="sxs-lookup"><span data-stu-id="0c794-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="0c794-184">Odesílání e-mailů v testovacím režimu</span><span class="sxs-lookup"><span data-stu-id="0c794-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="0c794-185">Tento fragment kódu ukazuje, jak nastavit vlastnosti dvou testů: `TestMailTo` nastavením na všechny zprávy se `john.doe@contoso.con` pošle (bez ohledu na hodnoty do, kopie, Skrytá kopie).</span><span class="sxs-lookup"><span data-stu-id="0c794-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="0c794-186">Nastavením TestDropPath všech odchozích e-mailů se také zaznamená v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="0c794-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="0c794-187">Tyto vlastnosti lze nastavit nezávisle (nejsou v relaci).</span><span class="sxs-lookup"><span data-stu-id="0c794-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="0c794-188">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="0c794-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="0c794-189">Pro tuto ukázku je vyžadován přístup k serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="0c794-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="0c794-190">Další informace o nastavení serveru SMTP najdete na následujících odkazech.</span><span class="sxs-lookup"><span data-stu-id="0c794-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- [<span data-ttu-id="0c794-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="0c794-191">Microsoft Technet</span></span>](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [<span data-ttu-id="0c794-192">Konfigurace služby SMTP (IIS 6,0)</span><span class="sxs-lookup"><span data-stu-id="0c794-192">Configuring the SMTP Service (IIS 6.0)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [<span data-ttu-id="0c794-193">IIS 7.0: Konfigurace e-mailu SMTP</span><span class="sxs-lookup"><span data-stu-id="0c794-193">IIS 7.0: Configure SMTP E-Mail</span></span>](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [<span data-ttu-id="0c794-194">Jak nainstalovat službu SMTP</span><span class="sxs-lookup"><span data-stu-id="0c794-194">How to Install the SMTP Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="0c794-195">Emulátory SMTP poskytované třetími stranami jsou k dispozici ke stažení.</span><span class="sxs-lookup"><span data-stu-id="0c794-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="0c794-196">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="0c794-196">To run this sample</span></span>  
  
1. <span data-ttu-id="0c794-197">Pomocí sady Visual Studio 2010 otevřete soubor řešení SendMail. sln.</span><span class="sxs-lookup"><span data-stu-id="0c794-197">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="0c794-198">Ujistěte se, že máte přístup k platnému serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="0c794-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="0c794-199">Projděte si pokyny pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="0c794-199">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="0c794-200">Nakonfigurujte program s adresou serveru, a to od a po e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="0c794-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="0c794-201">Pro správné spuštění této ukázky může být nutné nakonfigurovat hodnotu z a na e-mailové adresy a adresu serveru SMTP v Program.cs a Sequence. XAML.</span><span class="sxs-lookup"><span data-stu-id="0c794-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="0c794-202">Tuto adresu budete muset změnit v obou umístěních, protože program odesílá e-maily dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="0c794-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="0c794-203">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="0c794-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="0c794-204">Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="0c794-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0c794-205">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="0c794-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0c794-206">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="0c794-206">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="0c794-207">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="0c794-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0c794-208">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0c794-208">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
