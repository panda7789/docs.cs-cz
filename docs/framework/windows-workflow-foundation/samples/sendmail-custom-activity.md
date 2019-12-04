---
title: Vlastní aktivita SendMail
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: b1e2d58a09362569d4d408f6e1c9e589aa6bda76
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715571"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="f1f3a-102">Vlastní aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="f1f3a-102">SendMail Custom Activity</span></span>
<span data-ttu-id="f1f3a-103">V této ukázce se dozvíte, jak vytvořit vlastní aktivitu, která se odvozuje z <xref:System.Activities.AsyncCodeActivity> k odeslání e-mailu pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="f1f3a-104">Vlastní aktivita využívá možnosti <xref:System.Net.Mail.SmtpClient> k asynchronnímu posílání e-mailů a k odesílání e-mailů s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="f1f3a-105">Poskytuje také některé funkce koncového uživatele, jako je režim testu, nahrazení tokenu, šablony souborů a cesta pro vyřazení testu.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="f1f3a-106">Následující tabulka popisuje argumenty aktivity `SendMail`.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="f1f3a-107">Name</span><span class="sxs-lookup"><span data-stu-id="f1f3a-107">Name</span></span>|<span data-ttu-id="f1f3a-108">Type</span><span class="sxs-lookup"><span data-stu-id="f1f3a-108">Type</span></span>|<span data-ttu-id="f1f3a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f1f3a-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="f1f3a-110">Hostitel</span><span class="sxs-lookup"><span data-stu-id="f1f3a-110">Host</span></span>|<span data-ttu-id="f1f3a-111">String</span><span class="sxs-lookup"><span data-stu-id="f1f3a-111">String</span></span>|<span data-ttu-id="f1f3a-112">Adresa hostitele serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="f1f3a-113">Port</span><span class="sxs-lookup"><span data-stu-id="f1f3a-113">Port</span></span>|<span data-ttu-id="f1f3a-114">String</span><span class="sxs-lookup"><span data-stu-id="f1f3a-114">String</span></span>|<span data-ttu-id="f1f3a-115">Port služby SMTP v hostiteli.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="f1f3a-116">enableSsl</span><span class="sxs-lookup"><span data-stu-id="f1f3a-116">EnableSsl</span></span>|<span data-ttu-id="f1f3a-117">bool</span><span class="sxs-lookup"><span data-stu-id="f1f3a-117">bool</span></span>|<span data-ttu-id="f1f3a-118">Určuje, jestli <xref:System.Net.Mail.SmtpClient> k šifrování připojení používá SSL (Secure Sockets Layer) (SSL).</span><span class="sxs-lookup"><span data-stu-id="f1f3a-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="f1f3a-119">UserName</span><span class="sxs-lookup"><span data-stu-id="f1f3a-119">UserName</span></span>|<span data-ttu-id="f1f3a-120">String</span><span class="sxs-lookup"><span data-stu-id="f1f3a-120">String</span></span>|<span data-ttu-id="f1f3a-121">Uživatelské jméno pro nastavení přihlašovacích údajů pro ověření vlastnosti odesílatele <xref:System.Net.Mail.SmtpClient.Credentials%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="f1f3a-122">Heslo</span><span class="sxs-lookup"><span data-stu-id="f1f3a-122">Password</span></span>|<span data-ttu-id="f1f3a-123">String</span><span class="sxs-lookup"><span data-stu-id="f1f3a-123">String</span></span>|<span data-ttu-id="f1f3a-124">Heslo pro nastavení přihlašovacích údajů pro ověření vlastnosti odesílatele <xref:System.Net.Mail.SmtpClient.Credentials%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="f1f3a-125">Předmět</span><span class="sxs-lookup"><span data-stu-id="f1f3a-125">Subject</span></span>|<span data-ttu-id="f1f3a-126">řetězec \<<xref:System.Activities.InArgument%601></span><span class="sxs-lookup"><span data-stu-id="f1f3a-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f1f3a-127">Předmět zprávy</span><span class="sxs-lookup"><span data-stu-id="f1f3a-127">Subject of the message.</span></span>|  
|<span data-ttu-id="f1f3a-128">Text</span><span class="sxs-lookup"><span data-stu-id="f1f3a-128">Body</span></span>|<span data-ttu-id="f1f3a-129">řetězec \<<xref:System.Activities.InArgument%601></span><span class="sxs-lookup"><span data-stu-id="f1f3a-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f1f3a-130">Text zprávy</span><span class="sxs-lookup"><span data-stu-id="f1f3a-130">Body of the message.</span></span>|  
|<span data-ttu-id="f1f3a-131">Přílohy</span><span class="sxs-lookup"><span data-stu-id="f1f3a-131">Attachments</span></span>|<span data-ttu-id="f1f3a-132">řetězec \<<xref:System.Activities.InArgument%601></span><span class="sxs-lookup"><span data-stu-id="f1f3a-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="f1f3a-133">Kolekce příloh používaná k ukládání dat připojených k této e-mailové zprávě</span><span class="sxs-lookup"><span data-stu-id="f1f3a-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="f1f3a-134">Od</span><span class="sxs-lookup"><span data-stu-id="f1f3a-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="f1f3a-135">Z adresy pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-135">From address for this email message.</span></span>|  
|<span data-ttu-id="f1f3a-136">Pro</span><span class="sxs-lookup"><span data-stu-id="f1f3a-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f1f3a-137">Kolekce adres, která obsahuje příjemce této e-mailové zprávy.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="f1f3a-138">CC</span><span class="sxs-lookup"><span data-stu-id="f1f3a-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f1f3a-139">Kolekce adres, která obsahuje příjemce kopie (CC) pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="f1f3a-140">SKRYT</span><span class="sxs-lookup"><span data-stu-id="f1f3a-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="f1f3a-141">Kolekce adres, která obsahuje příjemce skryté kopie (BCC) pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="f1f3a-142">Tokeny</span><span class="sxs-lookup"><span data-stu-id="f1f3a-142">Tokens</span></span>|<span data-ttu-id="f1f3a-143"><xref:System.Activities.InArgument%601>< IDictionary\<String, String > ></span><span class="sxs-lookup"><span data-stu-id="f1f3a-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="f1f3a-144">Tokeny, které mají být nahrazeny v těle.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-144">Tokens to replace in the body.</span></span> <span data-ttu-id="f1f3a-145">Tato funkce umožňuje uživatelům zadat v těle některé hodnoty, než je lze později nahradit tokeny poskytnutými pomocí této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="f1f3a-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="f1f3a-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="f1f3a-147">String</span><span class="sxs-lookup"><span data-stu-id="f1f3a-147">String</span></span>|<span data-ttu-id="f1f3a-148">Cesta k šabloně pro tělo</span><span class="sxs-lookup"><span data-stu-id="f1f3a-148">Path of a template for the body.</span></span> <span data-ttu-id="f1f3a-149">Aktivita `SendMail` kopíruje obsah tohoto souboru do vlastnosti body.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="f1f3a-150">Šablona může obsahovat tokeny, které jsou nahrazeny obsahem vlastnosti tokeny.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="f1f3a-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="f1f3a-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="f1f3a-152">Když je tato vlastnost nastavená, všechny e-maily se odešlou na adresu uvedenou v ní.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="f1f3a-153">Tato vlastnost je určena pro použití při testování pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="f1f3a-154">Například pokud chcete zajistit, aby byly všechny e-maily odeslány bez jejich odeslání skutečným příjemcům.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="f1f3a-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="f1f3a-155">TestDropPath</span></span>|<span data-ttu-id="f1f3a-156">String</span><span class="sxs-lookup"><span data-stu-id="f1f3a-156">String</span></span>|<span data-ttu-id="f1f3a-157">Když je tato vlastnost nastavená, všechny e-maily se uloží i do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="f1f3a-158">Tato vlastnost je určena k použití při testování nebo ladění pracovních postupů, abyste se ujistili, že formát a obsah odchozích e-mailů je vhodný.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="f1f3a-159">Obsah řešení</span><span class="sxs-lookup"><span data-stu-id="f1f3a-159">Solution Contents</span></span>  
 <span data-ttu-id="f1f3a-160">Řešení obsahuje dva projekty.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="f1f3a-161">Projekt</span><span class="sxs-lookup"><span data-stu-id="f1f3a-161">Project</span></span>|<span data-ttu-id="f1f3a-162">Popis</span><span class="sxs-lookup"><span data-stu-id="f1f3a-162">Description</span></span>|<span data-ttu-id="f1f3a-163">Důležité soubory</span><span class="sxs-lookup"><span data-stu-id="f1f3a-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="f1f3a-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="f1f3a-164">SendMail</span></span>|<span data-ttu-id="f1f3a-165">Aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="f1f3a-165">The SendMail activity</span></span>|<span data-ttu-id="f1f3a-166">1. SendMail.cs: implementace hlavní aktivity</span><span class="sxs-lookup"><span data-stu-id="f1f3a-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="f1f3a-167">2. SendMailDesigner. XAML a SendMailDesigner.xaml.cs: Návrhář pro aktivitu SendMail</span><span class="sxs-lookup"><span data-stu-id="f1f3a-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="f1f3a-168">3. MailTemplateBody. htm: Šablona pro odeslání e-mailu.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="f1f3a-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="f1f3a-169">SendMailTestClient</span></span>|<span data-ttu-id="f1f3a-170">Klient pro otestování aktivity SendMail</span><span class="sxs-lookup"><span data-stu-id="f1f3a-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="f1f3a-171">Tento projekt znázorňuje dva způsoby volání aktivity SendMail: deklarativně a programově.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="f1f3a-172">1. Sequence1. XAML: pracovní postup, který vyvolá aktivitu SendMail.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="f1f3a-173">2. Program.cs: vyvolá Sequence1 a také vytvoří pracovní postup programově, který používá SendMail.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="f1f3a-174">Další konfigurace aktivity SendMail</span><span class="sxs-lookup"><span data-stu-id="f1f3a-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="f1f3a-175">I když v ukázce není zobrazený, můžou uživatelé provádět i konfiguraci aktivity SendMail.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="f1f3a-176">Další tři části ukazují, jak to uděláte.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="f1f3a-177">Odeslání e-mailu pomocí tokenů zadaných v těle</span><span class="sxs-lookup"><span data-stu-id="f1f3a-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="f1f3a-178">Tento fragment kódu ukazuje, jak můžete odeslat e-mail s tokeny v těle.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="f1f3a-179">Všimněte si, jak jsou tokeny k dispozici ve vlastnosti body.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="f1f3a-180">Hodnoty pro tyto tokeny jsou k dispozici pro vlastnost tokeny.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="f1f3a-181">Odeslání e-mailu pomocí šablony</span><span class="sxs-lookup"><span data-stu-id="f1f3a-181">Sending an email using a template</span></span>  
 <span data-ttu-id="f1f3a-182">Tento fragment kódu ukazuje, jak odeslat e-mail pomocí tokenů šablony v těle.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="f1f3a-183">Všimněte si, že při nastavování vlastnosti `BodyTemplateFilePath` nepotřebujeme zadat hodnotu vlastnosti tělo (obsah souboru šablony se zkopíruje do těla).</span><span class="sxs-lookup"><span data-stu-id="f1f3a-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="f1f3a-184">Odesílání e-mailů v testovacím režimu</span><span class="sxs-lookup"><span data-stu-id="f1f3a-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="f1f3a-185">Tento fragment kódu ukazuje, jak nastavit vlastnosti dvou testů: nastavením `TestMailTo` na všechny zprávy bude odesláno do `john.doe@contoso.con` (bez ohledu na hodnoty do, kopie, Skrytá kopie).</span><span class="sxs-lookup"><span data-stu-id="f1f3a-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="f1f3a-186">Nastavením TestDropPath všech odchozích e-mailů se také zaznamená v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="f1f3a-187">Tyto vlastnosti lze nastavit nezávisle (nejsou v relaci).</span><span class="sxs-lookup"><span data-stu-id="f1f3a-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="f1f3a-188">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="f1f3a-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="f1f3a-189">Pro tuto ukázku je vyžadován přístup k serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="f1f3a-190">Další informace o nastavení serveru SMTP najdete na následujících odkazech.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- [<span data-ttu-id="f1f3a-191">Microsoft TechNet</span><span class="sxs-lookup"><span data-stu-id="f1f3a-191">Microsoft Technet</span></span>](https://go.microsoft.com/fwlink/?LinkId=166060)  
  
- [<span data-ttu-id="f1f3a-192">Konfigurace služby SMTP (IIS 6,0)</span><span class="sxs-lookup"><span data-stu-id="f1f3a-192">Configuring the SMTP Service (IIS 6.0)</span></span>](https://go.microsoft.com/fwlink/?LinkId=150456)  
  
- [<span data-ttu-id="f1f3a-193">IIS 7,0: Konfigurace e-mailu SMTP</span><span class="sxs-lookup"><span data-stu-id="f1f3a-193">IIS 7.0: Configure SMTP E-Mail</span></span>](https://go.microsoft.com/fwlink/?LinkId=150457)  
  
- [<span data-ttu-id="f1f3a-194">Jak nainstalovat službu SMTP</span><span class="sxs-lookup"><span data-stu-id="f1f3a-194">How to Install the SMTP Service</span></span>](https://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="f1f3a-195">Emulátory SMTP poskytované třetími stranami jsou k dispozici ke stažení.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="f1f3a-196">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="f1f3a-196">To run this sample</span></span>  
  
1. <span data-ttu-id="f1f3a-197">Pomocí sady Visual Studio 2010 otevřete soubor řešení SendMail. sln.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-197">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="f1f3a-198">Ujistěte se, že máte přístup k platnému serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="f1f3a-199">Projděte si pokyny pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-199">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="f1f3a-200">Nakonfigurujte program s adresou serveru, a to od a po e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-200">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="f1f3a-201">Pro správné spuštění této ukázky může být nutné nakonfigurovat hodnotu z a na e-mailové adresy a adresu serveru SMTP v Program.cs a Sequence. XAML.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-201">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="f1f3a-202">Tuto adresu budete muset změnit v obou umístěních, protože program odesílá e-maily dvěma různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="f1f3a-203">Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="f1f3a-204">Pokud chcete řešení spustit, stiskněte klávesy CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f1f3a-205">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f1f3a-206">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-206">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f1f3a-207">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f1f3a-208">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f1f3a-208">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
