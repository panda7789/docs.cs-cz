---
title: Vlastní aktivita SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: e9d27711754c3aa8ff7f68c23f528c9f5c4356f7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43533870"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="fa732-102">Vlastní aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="fa732-102">SendMail Custom Activity</span></span>
<span data-ttu-id="fa732-103">Tato ukázka předvádí, jak vytvořit vlastní aktivitu, která je odvozena z <xref:System.Activities.AsyncCodeActivity> k odesílání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="fa732-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="fa732-104">Vlastní aktivita používá možnosti <xref:System.Net.Mail.SmtpClient> asynchronní odeslání e-mailu a odesílání e-mailu s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="fa732-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="fa732-105">Poskytuje také některé funkce koncových uživatelů, jako je režim, nahrazování tokenů, soubor šablony a testujte cestu pro přetažení.</span><span class="sxs-lookup"><span data-stu-id="fa732-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="fa732-106">Následující tabulka obsahuje podrobnosti o argumenty `SendMail` aktivity.</span><span class="sxs-lookup"><span data-stu-id="fa732-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="fa732-107">Název</span><span class="sxs-lookup"><span data-stu-id="fa732-107">Name</span></span>|<span data-ttu-id="fa732-108">Typ</span><span class="sxs-lookup"><span data-stu-id="fa732-108">Type</span></span>|<span data-ttu-id="fa732-109">Popis</span><span class="sxs-lookup"><span data-stu-id="fa732-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="fa732-110">Hostitel</span><span class="sxs-lookup"><span data-stu-id="fa732-110">Host</span></span>|<span data-ttu-id="fa732-111">String</span><span class="sxs-lookup"><span data-stu-id="fa732-111">String</span></span>|<span data-ttu-id="fa732-112">Adresa hostitele serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="fa732-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="fa732-113">Port</span><span class="sxs-lookup"><span data-stu-id="fa732-113">Port</span></span>|<span data-ttu-id="fa732-114">String</span><span class="sxs-lookup"><span data-stu-id="fa732-114">String</span></span>|<span data-ttu-id="fa732-115">Port služby SMTP na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="fa732-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="fa732-116">enableSsl</span><span class="sxs-lookup"><span data-stu-id="fa732-116">EnableSsl</span></span>|<span data-ttu-id="fa732-117">bool</span><span class="sxs-lookup"><span data-stu-id="fa732-117">bool</span></span>|<span data-ttu-id="fa732-118">Určuje, zda <xref:System.Net.Mail.SmtpClient> vrstvy SSL (Secure Sockets) používá k šifrování připojení.</span><span class="sxs-lookup"><span data-stu-id="fa732-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="fa732-119">UserName</span><span class="sxs-lookup"><span data-stu-id="fa732-119">UserName</span></span>|<span data-ttu-id="fa732-120">String</span><span class="sxs-lookup"><span data-stu-id="fa732-120">String</span></span>|<span data-ttu-id="fa732-121">Uživatelské jméno pro nastavení přihlašovacích údajů pro ověření odesílatel <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fa732-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="fa732-122">Heslo</span><span class="sxs-lookup"><span data-stu-id="fa732-122">Password</span></span>|<span data-ttu-id="fa732-123">String</span><span class="sxs-lookup"><span data-stu-id="fa732-123">String</span></span>|<span data-ttu-id="fa732-124">Heslo k nastavení pověření pro ověření odesílatel <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="fa732-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="fa732-125">Předmět</span><span class="sxs-lookup"><span data-stu-id="fa732-125">Subject</span></span>|<span data-ttu-id="fa732-126"><xref:System.Activities.InArgument%601>\<řetězec ></span><span class="sxs-lookup"><span data-stu-id="fa732-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="fa732-127">Předmět zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa732-127">Subject of the message.</span></span>|  
|<span data-ttu-id="fa732-128">Text</span><span class="sxs-lookup"><span data-stu-id="fa732-128">Body</span></span>|<span data-ttu-id="fa732-129"><xref:System.Activities.InArgument%601>\<řetězec ></span><span class="sxs-lookup"><span data-stu-id="fa732-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="fa732-130">Text zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa732-130">Body of the message.</span></span>|  
|<span data-ttu-id="fa732-131">Přílohy</span><span class="sxs-lookup"><span data-stu-id="fa732-131">Attachments</span></span>|<span data-ttu-id="fa732-132"><xref:System.Activities.InArgument%601>\<řetězec ></span><span class="sxs-lookup"><span data-stu-id="fa732-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="fa732-133">Kolekce přílohy sloužící k ukládání dat, které jsou připojené k této e-mailové zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa732-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="fa732-134">From</span><span class="sxs-lookup"><span data-stu-id="fa732-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="fa732-135">Z adresy pro tento e-mailové zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa732-135">From address for this email message.</span></span>|  
|<span data-ttu-id="fa732-136">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="fa732-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="fa732-137">Kolekce adres, který obsahuje příjemci tohoto e-mailové zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa732-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="fa732-138">CC</span><span class="sxs-lookup"><span data-stu-id="fa732-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="fa732-139">Adresa kolekce, která obsahuje příjemci kopie (CC) pro tento e-mailové zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa732-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="fa732-140">BCC</span><span class="sxs-lookup"><span data-stu-id="fa732-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="fa732-141">Kolekce adres, který obsahuje příjemci skryté kopie (SKRYTÁ) pro tento e-mailové zprávy.</span><span class="sxs-lookup"><span data-stu-id="fa732-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="fa732-142">Tokeny</span><span class="sxs-lookup"><span data-stu-id="fa732-142">Tokens</span></span>|<span data-ttu-id="fa732-143"><xref:System.Activities.InArgument%601>< IDictionary\<řetězec, řetězec >></span><span class="sxs-lookup"><span data-stu-id="fa732-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="fa732-144">Tokeny pro nahrazení v textu.</span><span class="sxs-lookup"><span data-stu-id="fa732-144">Tokens to replace in the body.</span></span> <span data-ttu-id="fa732-145">Tato funkce umožňuje uživatelům zadat některé hodnoty v textu, než lze později nahradit tokeny k dispozici pomocí této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="fa732-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="fa732-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="fa732-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="fa732-147">String</span><span class="sxs-lookup"><span data-stu-id="fa732-147">String</span></span>|<span data-ttu-id="fa732-148">Cesta k šabloně pro tělo.</span><span class="sxs-lookup"><span data-stu-id="fa732-148">Path of a template for the body.</span></span> <span data-ttu-id="fa732-149">`SendMail` Aktivita kopíruje obsah tohoto souboru do jeho vlastnosti body.</span><span class="sxs-lookup"><span data-stu-id="fa732-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="fa732-150">Šablona může obsahovat tokeny, které jsou nahrazeny obsah vlastnosti tokeny.</span><span class="sxs-lookup"><span data-stu-id="fa732-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="fa732-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="fa732-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="fa732-152">Pokud je tato vlastnost nastavena, všechny e-maily se odesílají na adresu zadanou v ní.</span><span class="sxs-lookup"><span data-stu-id="fa732-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="fa732-153">Tato vlastnost je určena pro použití při testování pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="fa732-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="fa732-154">Například pokud chcete Ujistěte se, že všechny mailů bez odeslání skutečné příjemcům.</span><span class="sxs-lookup"><span data-stu-id="fa732-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="fa732-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="fa732-155">TestDropPath</span></span>|<span data-ttu-id="fa732-156">String</span><span class="sxs-lookup"><span data-stu-id="fa732-156">String</span></span>|<span data-ttu-id="fa732-157">Pokud je tato vlastnost nastavena, všechny e-maily jsou také uloženy ve zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="fa732-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="fa732-158">Tato vlastnost je určena pro použití při testování nebo ladění pracovních postupů, abyste měli jistotu, že je příslušný formát a obsah odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="fa732-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="fa732-159">Obsah řešení</span><span class="sxs-lookup"><span data-stu-id="fa732-159">Solution Contents</span></span>  
 <span data-ttu-id="fa732-160">Řešení obsahuje dva projekty.</span><span class="sxs-lookup"><span data-stu-id="fa732-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="fa732-161">Projekt</span><span class="sxs-lookup"><span data-stu-id="fa732-161">Project</span></span>|<span data-ttu-id="fa732-162">Popis</span><span class="sxs-lookup"><span data-stu-id="fa732-162">Description</span></span>|<span data-ttu-id="fa732-163">Důležitých souborů</span><span class="sxs-lookup"><span data-stu-id="fa732-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="fa732-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="fa732-164">SendMail</span></span>|<span data-ttu-id="fa732-165">Aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="fa732-165">The SendMail activity</span></span>|<span data-ttu-id="fa732-166">1.  SendMail.cs: implementace pro hlavní aktivitu</span><span class="sxs-lookup"><span data-stu-id="fa732-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="fa732-167">2.  SendMailDesigner.xaml a SendMailDesigner.xaml.cs: návrháře pro aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="fa732-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="fa732-168">3.  MailTemplateBody.htm: Šablona e-mailu k odeslání.</span><span class="sxs-lookup"><span data-stu-id="fa732-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="fa732-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="fa732-169">SendMailTestClient</span></span>|<span data-ttu-id="fa732-170">Testovací aktivita SendMail klienta.</span><span class="sxs-lookup"><span data-stu-id="fa732-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="fa732-171">Tento projekt ukazuje dva způsoby volání aktivita SendMail: deklarativně a prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="fa732-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="fa732-172">1.  Sequence1.XAML: pracovní postup, který volá aktivita SendMail.</span><span class="sxs-lookup"><span data-stu-id="fa732-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="fa732-173">2.  Soubor program.cs: vyvolá Sequence1 a také vytvoří pracovní postup prostřednictvím kódu programu, který používá SendMail.</span><span class="sxs-lookup"><span data-stu-id="fa732-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="fa732-174">Další konfigurace aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="fa732-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="fa732-175">I když není zobrazený ve vzorku, uživatelé mohou provádět přidání konfigurace aktivita SendMail.</span><span class="sxs-lookup"><span data-stu-id="fa732-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="fa732-176">V následujících třech částech ukazují, jak to lze provést.</span><span class="sxs-lookup"><span data-stu-id="fa732-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="fa732-177">Odesílání e-mailu pomocí tokenů zadaná v těle</span><span class="sxs-lookup"><span data-stu-id="fa732-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="fa732-178">Tento fragment kódu ukazuje, jak můžete poslat e-mailu s tokeny v textu.</span><span class="sxs-lookup"><span data-stu-id="fa732-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="fa732-179">Všimněte si, jak jsou k dispozici tokeny ve vlastnosti tělo.</span><span class="sxs-lookup"><span data-stu-id="fa732-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="fa732-180">Hodnoty pro tyto tokeny jsou k dispozici na vlastnost tokeny.</span><span class="sxs-lookup"><span data-stu-id="fa732-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="fa732-181">Odesílání e-mailu pomocí šablony</span><span class="sxs-lookup"><span data-stu-id="fa732-181">Sending an email using a template</span></span>  
 <span data-ttu-id="fa732-182">Tento fragment kódu ukazuje, jak odesílat e-maily pomocí šablony tokeny v textu.</span><span class="sxs-lookup"><span data-stu-id="fa732-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="fa732-183">Všimněte si, že při nastavení `BodyTemplateFilePath` vlastnost nemusíme poskytovat hodnotu pro vlastnost text (obsah souboru šablony se zkopíruje do textu).</span><span class="sxs-lookup"><span data-stu-id="fa732-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="fa732-184">Odesílání e-mailů při testování režimu</span><span class="sxs-lookup"><span data-stu-id="fa732-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="fa732-185">Tento fragment kódu ukazuje, jak nastavit vlastnosti testování dvě: nastavením `TestMailTo` pro všechny zprávy se odešlou do john.doe@contoso.con (bez ohledu na hodnoty Komu, kopie, skrytá).</span><span class="sxs-lookup"><span data-stu-id="fa732-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to john.doe@contoso.con (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="fa732-186">Nastavením TestDropPath se také zaznamená všechny odchozí e-mailů v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="fa732-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="fa732-187">Tyto vlastnosti můžete nastavit samostatně (nesouvisí).</span><span class="sxs-lookup"><span data-stu-id="fa732-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="fa732-188">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="fa732-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="fa732-189">Přístup k serveru SMTP je vyžadován pro tuto ukázku.</span><span class="sxs-lookup"><span data-stu-id="fa732-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="fa732-190">Další informace o nastavení serveru SMTP najdete na následujících odkazech.</span><span class="sxs-lookup"><span data-stu-id="fa732-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="fa732-191">Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="fa732-191">Microsoft Technet</span></span>](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="fa732-192">Konfigurace SMTP služby (IIS 6.0)</span><span class="sxs-lookup"><span data-stu-id="fa732-192">Configuring the SMTP Service (IIS 6.0)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="fa732-193">Služba IIS 7.0: Konfigurace e-mailu SMTP</span><span class="sxs-lookup"><span data-stu-id="fa732-193">IIS 7.0: Configure SMTP E-Mail</span></span>](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="fa732-194">Jak nainstalovat službu SMTP</span><span class="sxs-lookup"><span data-stu-id="fa732-194">How to Install the SMTP Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="fa732-195">Emulátory SMTP třetích stran jsou k dispozici ke stažení.</span><span class="sxs-lookup"><span data-stu-id="fa732-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="fa732-196">Tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="fa732-196">To run this sample</span></span>  
  
1.  <span data-ttu-id="fa732-197">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="fa732-197">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SendMail.sln solution file.</span></span>  
  
2.  <span data-ttu-id="fa732-198">Ujistěte se, že máte přístup k SMTP serveru platný.</span><span class="sxs-lookup"><span data-stu-id="fa732-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="fa732-199">Zobrazit pokyny k instalaci.</span><span class="sxs-lookup"><span data-stu-id="fa732-199">See the set-up instructions.</span></span>  
  
3.  <span data-ttu-id="fa732-200">Konfigurace programu s adresu serveru a od a do e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="fa732-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="fa732-201">Pro správné spuštění této ukázky, budete muset nakonfigurovat hodnotu od a do e-mailové adresy a adresu serveru SMTP v souboru Program.cs a Sequence.xaml.</span><span class="sxs-lookup"><span data-stu-id="fa732-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="fa732-202">Budete muset změnit adresu i v cloudu, protože program odešle e-mailu dvěma různými způsoby</span><span class="sxs-lookup"><span data-stu-id="fa732-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4.  <span data-ttu-id="fa732-203">Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="fa732-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="fa732-204">Abyste mohli spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="fa732-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fa732-205">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="fa732-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fa732-206">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="fa732-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fa732-207">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="fa732-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fa732-208">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="fa732-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`