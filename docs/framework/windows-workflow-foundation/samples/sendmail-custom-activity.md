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
# <a name="sendmail-custom-activity"></a><span data-ttu-id="6c01d-102">Vlastní aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="6c01d-102">SendMail Custom Activity</span></span>
<span data-ttu-id="6c01d-103">Tato ukázka ukazuje, jak vytvořit vlastní <xref:System.Activities.AsyncCodeActivity> aktivitu, která je odvozena od odesílání pošty pomocí protokolu SMTP pro použití v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="6c01d-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="6c01d-104">Vlastní aktivita využívá <xref:System.Net.Mail.SmtpClient> možnosti odesílání e-mailu asynchronně a odesílání pošty s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6c01d-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="6c01d-105">Poskytuje také některé funkce koncového uživatele, jako je testovací režim, nahrazení tokenu, šablony souborů a cesta k přetažení testu.</span><span class="sxs-lookup"><span data-stu-id="6c01d-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="6c01d-106">V následující tabulce jsou podrobně `SendMail` uvedeny argumenty pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="6c01d-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="6c01d-107">Name (Název)</span><span class="sxs-lookup"><span data-stu-id="6c01d-107">Name</span></span>|<span data-ttu-id="6c01d-108">Typ</span><span class="sxs-lookup"><span data-stu-id="6c01d-108">Type</span></span>|<span data-ttu-id="6c01d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6c01d-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="6c01d-110">Hostitel</span><span class="sxs-lookup"><span data-stu-id="6c01d-110">Host</span></span>|<span data-ttu-id="6c01d-111">Řetězec</span><span class="sxs-lookup"><span data-stu-id="6c01d-111">String</span></span>|<span data-ttu-id="6c01d-112">Adresa hostitele serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="6c01d-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="6c01d-113">Port</span><span class="sxs-lookup"><span data-stu-id="6c01d-113">Port</span></span>|<span data-ttu-id="6c01d-114">Řetězec</span><span class="sxs-lookup"><span data-stu-id="6c01d-114">String</span></span>|<span data-ttu-id="6c01d-115">Port služby SMTP v hostiteli.</span><span class="sxs-lookup"><span data-stu-id="6c01d-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="6c01d-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="6c01d-116">EnableSsl</span></span>|<span data-ttu-id="6c01d-117">bool</span><span class="sxs-lookup"><span data-stu-id="6c01d-117">bool</span></span>|<span data-ttu-id="6c01d-118">Určuje, <xref:System.Net.Mail.SmtpClient> zda k šifrování připojení používá ssl (Secure Sockets Layer).</span><span class="sxs-lookup"><span data-stu-id="6c01d-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="6c01d-119">UserName</span><span class="sxs-lookup"><span data-stu-id="6c01d-119">UserName</span></span>|<span data-ttu-id="6c01d-120">Řetězec</span><span class="sxs-lookup"><span data-stu-id="6c01d-120">String</span></span>|<span data-ttu-id="6c01d-121">Uživatelské jméno pro nastavení pověření k ověření <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnosti odesílatele.</span><span class="sxs-lookup"><span data-stu-id="6c01d-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="6c01d-122">Heslo</span><span class="sxs-lookup"><span data-stu-id="6c01d-122">Password</span></span>|<span data-ttu-id="6c01d-123">Řetězec</span><span class="sxs-lookup"><span data-stu-id="6c01d-123">String</span></span>|<span data-ttu-id="6c01d-124">Heslo pro nastavení pověření k ověření <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnosti odesílatele.</span><span class="sxs-lookup"><span data-stu-id="6c01d-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="6c01d-125">Subjekt</span><span class="sxs-lookup"><span data-stu-id="6c01d-125">Subject</span></span>|<span data-ttu-id="6c01d-126"><xref:System.Activities.InArgument%601>\<řetězec></span><span class="sxs-lookup"><span data-stu-id="6c01d-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="6c01d-127">Předmět zprávy.</span><span class="sxs-lookup"><span data-stu-id="6c01d-127">Subject of the message.</span></span>|  
|<span data-ttu-id="6c01d-128">Tělo</span><span class="sxs-lookup"><span data-stu-id="6c01d-128">Body</span></span>|<span data-ttu-id="6c01d-129"><xref:System.Activities.InArgument%601>\<řetězec></span><span class="sxs-lookup"><span data-stu-id="6c01d-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="6c01d-130">Text zprávy.</span><span class="sxs-lookup"><span data-stu-id="6c01d-130">Body of the message.</span></span>|  
|<span data-ttu-id="6c01d-131">Přílohy</span><span class="sxs-lookup"><span data-stu-id="6c01d-131">Attachments</span></span>|<span data-ttu-id="6c01d-132"><xref:System.Activities.InArgument%601>\<řetězec></span><span class="sxs-lookup"><span data-stu-id="6c01d-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="6c01d-133">Kolekce příloh používaná k ukládání dat připojených k této e-mailové zprávě.</span><span class="sxs-lookup"><span data-stu-id="6c01d-133">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="6c01d-134">From</span><span class="sxs-lookup"><span data-stu-id="6c01d-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="6c01d-135">Z adresy pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="6c01d-135">From address for this email message.</span></span>|  
|<span data-ttu-id="6c01d-136">Akce</span><span class="sxs-lookup"><span data-stu-id="6c01d-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="6c01d-137">Kolekce adres, která obsahuje příjemce této e-mailové zprávy.</span><span class="sxs-lookup"><span data-stu-id="6c01d-137">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="6c01d-138">CC</span><span class="sxs-lookup"><span data-stu-id="6c01d-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="6c01d-139">Kolekce adres, která obsahuje příjemce kopie (CC) pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="6c01d-139">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="6c01d-140">Skrytá</span><span class="sxs-lookup"><span data-stu-id="6c01d-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="6c01d-141">Kolekce adres, která obsahuje skryté uhlíkové kopie (SKRYTÁ) příjemci pro tuto e-mailovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="6c01d-141">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="6c01d-142">Tokeny</span><span class="sxs-lookup"><span data-stu-id="6c01d-142">Tokens</span></span>|<span data-ttu-id="6c01d-143"><xref:System.Activities.InArgument%601><Řetězec\<IDictionary, řetězec>></span><span class="sxs-lookup"><span data-stu-id="6c01d-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="6c01d-144">Tokeny nahradit v těle.</span><span class="sxs-lookup"><span data-stu-id="6c01d-144">Tokens to replace in the body.</span></span> <span data-ttu-id="6c01d-145">Tato funkce umožňuje uživatelům zadat některé hodnoty v těle, než může být nahrazen později tokeny poskytované pomocí této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6c01d-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="6c01d-146">Cesta BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="6c01d-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="6c01d-147">Řetězec</span><span class="sxs-lookup"><span data-stu-id="6c01d-147">String</span></span>|<span data-ttu-id="6c01d-148">Cesta šablony pro tělo.</span><span class="sxs-lookup"><span data-stu-id="6c01d-148">Path of a template for the body.</span></span> <span data-ttu-id="6c01d-149">Aktivita `SendMail` zkopíruje obsah tohoto souboru do jeho vlastnosti těla.</span><span class="sxs-lookup"><span data-stu-id="6c01d-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="6c01d-150">Šablona může obsahovat tokeny, které jsou nahrazeny obsahem vlastnosti tokeny.</span><span class="sxs-lookup"><span data-stu-id="6c01d-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="6c01d-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="6c01d-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="6c01d-152">Pokud je tato vlastnost nastavena, všechny e-maily jsou odesílány na adresu uvedenou v něm.</span><span class="sxs-lookup"><span data-stu-id="6c01d-152">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="6c01d-153">Tato vlastnost je určena pro použití při testování pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="6c01d-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="6c01d-154">Například pokud chcete zajistit, aby všechny e-maily byly odeslány bez jejich odeslání skutečným příjemcům.</span><span class="sxs-lookup"><span data-stu-id="6c01d-154">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="6c01d-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="6c01d-155">TestDropPath</span></span>|<span data-ttu-id="6c01d-156">Řetězec</span><span class="sxs-lookup"><span data-stu-id="6c01d-156">String</span></span>|<span data-ttu-id="6c01d-157">Pokud je tato vlastnost nastavena, všechny e-maily jsou také uloženy v zadaném souboru.</span><span class="sxs-lookup"><span data-stu-id="6c01d-157">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="6c01d-158">Tato vlastnost je určena pro použití při testování nebo ladění pracovních postupů, abyste se ujistili, že formát a obsah odchozích e-mailů je vhodný.</span><span class="sxs-lookup"><span data-stu-id="6c01d-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="6c01d-159">Obsah roztoku</span><span class="sxs-lookup"><span data-stu-id="6c01d-159">Solution Contents</span></span>  
 <span data-ttu-id="6c01d-160">Řešení obsahuje dva projekty.</span><span class="sxs-lookup"><span data-stu-id="6c01d-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="6c01d-161">Project</span><span class="sxs-lookup"><span data-stu-id="6c01d-161">Project</span></span>|<span data-ttu-id="6c01d-162">Popis</span><span class="sxs-lookup"><span data-stu-id="6c01d-162">Description</span></span>|<span data-ttu-id="6c01d-163">Důležité soubory</span><span class="sxs-lookup"><span data-stu-id="6c01d-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="6c01d-164">Sendmail</span><span class="sxs-lookup"><span data-stu-id="6c01d-164">SendMail</span></span>|<span data-ttu-id="6c01d-165">Aktivita SendMail</span><span class="sxs-lookup"><span data-stu-id="6c01d-165">The SendMail activity</span></span>|<span data-ttu-id="6c01d-166">1. SendMail.cs: provádění hlavní činnosti</span><span class="sxs-lookup"><span data-stu-id="6c01d-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="6c01d-167">2. SendMailDesigner.xaml a SendMailDesigner.xaml.cs: návrhář pro sendmail aktivitu</span><span class="sxs-lookup"><span data-stu-id="6c01d-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="6c01d-168">3. MailTemplateBody.htm: šablona pro e-mail, který má být odeslán.</span><span class="sxs-lookup"><span data-stu-id="6c01d-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="6c01d-169">OdeslatklientMailTest</span><span class="sxs-lookup"><span data-stu-id="6c01d-169">SendMailTestClient</span></span>|<span data-ttu-id="6c01d-170">Klient otestovat SendMail aktivitu.</span><span class="sxs-lookup"><span data-stu-id="6c01d-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="6c01d-171">Tento projekt ukazuje dva způsoby vyvolání SendMail aktivity: deklarativně a programově.</span><span class="sxs-lookup"><span data-stu-id="6c01d-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="6c01d-172">1. Sequence1.xaml: pracovní postup, který vyvolá sendmail aktivitu.</span><span class="sxs-lookup"><span data-stu-id="6c01d-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="6c01d-173">2. Program.cs: vyvolá Sequence1 a také vytvoří programově pracovní postup, který používá SendMail.</span><span class="sxs-lookup"><span data-stu-id="6c01d-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="6c01d-174">Další konfigurace aktivity SendMail</span><span class="sxs-lookup"><span data-stu-id="6c01d-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="6c01d-175">Ačkoli nejsou zobrazeny v ukázce, uživatelé mohou provádět přidání konfigurace SendMail aktivity.</span><span class="sxs-lookup"><span data-stu-id="6c01d-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="6c01d-176">Následující tři části ukazují, jak se to dělá.</span><span class="sxs-lookup"><span data-stu-id="6c01d-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="6c01d-177">Odeslání e-mailu pomocí tokenů určených v těle</span><span class="sxs-lookup"><span data-stu-id="6c01d-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="6c01d-178">Tento fragment kódu ukazuje, jak můžete odesílat e-maily s tokeny v těle.</span><span class="sxs-lookup"><span data-stu-id="6c01d-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="6c01d-179">Všimněte si, jak tokeny jsou k dispozici v těle vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6c01d-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="6c01d-180">Hodnoty pro tyto tokeny jsou k dispozici tokeny vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6c01d-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="6c01d-181">Odeslání e-mailu pomocí šablony</span><span class="sxs-lookup"><span data-stu-id="6c01d-181">Sending an email using a template</span></span>  
 <span data-ttu-id="6c01d-182">Tento úryvek ukazuje, jak odeslat e-mail pomocí tokenů šablony v těle.</span><span class="sxs-lookup"><span data-stu-id="6c01d-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="6c01d-183">Všimněte si, `BodyTemplateFilePath` že při nastavování vlastnosti nemusíme poskytovat hodnotu vlastnosti Body (obsah souboru šablony bude zkopírován do těla).</span><span class="sxs-lookup"><span data-stu-id="6c01d-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="6c01d-184">Odesílání e-mailů v testovacím režimu</span><span class="sxs-lookup"><span data-stu-id="6c01d-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="6c01d-185">Tento fragment kódu ukazuje, jak nastavit dvě vlastnosti `TestMailTo` testování: nastavením `john.doe@contoso.con` na všechny zprávy budou odeslány do (bez ohledu na hodnoty To, Kopie, Skrytá).</span><span class="sxs-lookup"><span data-stu-id="6c01d-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="6c01d-186">Nastavením TestDropPath všechny odchozí e-maily budou také zaznamenány v poskytnuté cestě.</span><span class="sxs-lookup"><span data-stu-id="6c01d-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="6c01d-187">Tyto vlastnosti lze nastavit nezávisle (nesouvisí).</span><span class="sxs-lookup"><span data-stu-id="6c01d-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="6c01d-188">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="6c01d-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="6c01d-189">Pro tuto ukázku je vyžadován přístup k serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="6c01d-189">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="6c01d-190">Další informace o nastavení serveru SMTP naleznete v následujících odkazech.</span><span class="sxs-lookup"><span data-stu-id="6c01d-190">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="6c01d-191">[Konfigurace služby SMTP (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="6c01d-191">[Configuring the SMTP Service (IIS 6.0)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="6c01d-192">[IIS 7.0: Konfigurace e-mailu SMTP](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="6c01d-192">[IIS 7.0: Configure SMTP E-Mail](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="6c01d-193">[Jak nainstalovat službu SMTP](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="6c01d-193">[How to Install the SMTP Service](https://docs.microsoft.com/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="6c01d-194">Emulátory SMTP poskytované třetími stranami jsou k dispozici ke stažení.</span><span class="sxs-lookup"><span data-stu-id="6c01d-194">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="6c01d-195">Spuštění této ukázky</span><span class="sxs-lookup"><span data-stu-id="6c01d-195">To run this sample</span></span>  
  
1. <span data-ttu-id="6c01d-196">Pomocí sady Visual Studio 2010 otevřete soubor řešení SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="6c01d-196">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="6c01d-197">Ujistěte se, že máte přístup k platnému serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="6c01d-197">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="6c01d-198">Podívejte se na pokyny k nastavení.</span><span class="sxs-lookup"><span data-stu-id="6c01d-198">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="6c01d-199">Nakonfigurujte program pomocí adresy serveru a e-mailových adres Od a Do.</span><span class="sxs-lookup"><span data-stu-id="6c01d-199">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="6c01d-200">Chcete-li správně spustit tuto ukázku, bude pravděpodobně nutné nakonfigurovat hodnotu e-mailových adres From a To a adresu serveru SMTP v Program.cs a v Sequence.xaml.</span><span class="sxs-lookup"><span data-stu-id="6c01d-200">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="6c01d-201">Budete muset změnit adresu v obou místech, protože program odesílá poštu dvěma různými způsoby</span><span class="sxs-lookup"><span data-stu-id="6c01d-201">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="6c01d-202">Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="6c01d-202">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="6c01d-203">Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="6c01d-203">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6c01d-204">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="6c01d-204">The samples may already be installed on your machine.</span></span> <span data-ttu-id="6c01d-205">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="6c01d-205">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="6c01d-206">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="6c01d-206">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="6c01d-207">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="6c01d-207">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
