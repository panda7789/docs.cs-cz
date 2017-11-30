---
title: "SendMail vlastní aktivity"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0e4501a4d1e9524a3631b29dba3cfee58bea5129
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="cb7d7-102">SendMail vlastní aktivity</span><span class="sxs-lookup"><span data-stu-id="cb7d7-102">SendMail Custom Activity</span></span>
<span data-ttu-id="cb7d7-103">Tento příklad ukazuje, jak vytvořit vlastní aktivitu, která je odvozena od <xref:System.Activities.AsyncCodeActivity> k odesílání pošty přes protokol SMTP pro použití v rámci aplikace pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="cb7d7-104">Vlastní aktivita používá možnosti <xref:System.Net.Mail.SmtpClient> asynchronně odesílat e-mailu a odesílat e-maily s ověřováním.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send e-mail asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="cb7d7-105">Poskytuje také některé funkce koncového uživatele jako testování režim tokenu nahrazení, soubor šablony a otestovat rozevírací cestu.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="cb7d7-106">V následující tabulce jsou argumenty `SendMail` aktivity.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="cb7d7-107">Název</span><span class="sxs-lookup"><span data-stu-id="cb7d7-107">Name</span></span>|<span data-ttu-id="cb7d7-108">Typ</span><span class="sxs-lookup"><span data-stu-id="cb7d7-108">Type</span></span>|<span data-ttu-id="cb7d7-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cb7d7-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="cb7d7-110">Hostitel</span><span class="sxs-lookup"><span data-stu-id="cb7d7-110">Host</span></span>|<span data-ttu-id="cb7d7-111">String</span><span class="sxs-lookup"><span data-stu-id="cb7d7-111">String</span></span>|<span data-ttu-id="cb7d7-112">Adresa hostitele serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="cb7d7-113">port</span><span class="sxs-lookup"><span data-stu-id="cb7d7-113">Port</span></span>|<span data-ttu-id="cb7d7-114">String</span><span class="sxs-lookup"><span data-stu-id="cb7d7-114">String</span></span>|<span data-ttu-id="cb7d7-115">Port služby SMTP na hostiteli.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="cb7d7-116">enableSsl</span><span class="sxs-lookup"><span data-stu-id="cb7d7-116">EnableSsl</span></span>|<span data-ttu-id="cb7d7-117">bool</span><span class="sxs-lookup"><span data-stu-id="cb7d7-117">bool</span></span>|<span data-ttu-id="cb7d7-118">Určuje, zda <xref:System.Net.Mail.SmtpClient> používá k šifrování připojení Secure Sockets Layer (SSL).</span><span class="sxs-lookup"><span data-stu-id="cb7d7-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="cb7d7-119">UserName</span><span class="sxs-lookup"><span data-stu-id="cb7d7-119">UserName</span></span>|<span data-ttu-id="cb7d7-120">String</span><span class="sxs-lookup"><span data-stu-id="cb7d7-120">String</span></span>|<span data-ttu-id="cb7d7-121">Uživatelské jméno k nastavení pověření pro ověření odesílatel <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="cb7d7-122">Heslo</span><span class="sxs-lookup"><span data-stu-id="cb7d7-122">Password</span></span>|<span data-ttu-id="cb7d7-123">String</span><span class="sxs-lookup"><span data-stu-id="cb7d7-123">String</span></span>|<span data-ttu-id="cb7d7-124">Heslo k nastavení pověření pro ověření odesílatel <xref:System.Net.Mail.SmtpClient.Credentials%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="cb7d7-125">Předmět</span><span class="sxs-lookup"><span data-stu-id="cb7d7-125">Subject</span></span>|<span data-ttu-id="cb7d7-126"><xref:System.Activities.InArgument%601>\<řetězec ></span><span class="sxs-lookup"><span data-stu-id="cb7d7-126"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="cb7d7-127">Předmět zprávy.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-127">Subject of the message.</span></span>|  
|<span data-ttu-id="cb7d7-128">Text</span><span class="sxs-lookup"><span data-stu-id="cb7d7-128">Body</span></span>|<span data-ttu-id="cb7d7-129"><xref:System.Activities.InArgument%601>\<řetězec ></span><span class="sxs-lookup"><span data-stu-id="cb7d7-129"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="cb7d7-130">Text zprávy.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-130">Body of the message.</span></span>|  
|<span data-ttu-id="cb7d7-131">Přílohy</span><span class="sxs-lookup"><span data-stu-id="cb7d7-131">Attachments</span></span>|<span data-ttu-id="cb7d7-132"><xref:System.Activities.InArgument%601>\<řetězec ></span><span class="sxs-lookup"><span data-stu-id="cb7d7-132"><xref:System.Activities.InArgument%601>\<string></span></span>|<span data-ttu-id="cb7d7-133">Kolekce přílohy používají k ukládání dat, které jsou připojené k této e-mailová zpráva.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-133">Attachment collection used to store data attached to this e-mail message.</span></span>|  
|<span data-ttu-id="cb7d7-134">From</span><span class="sxs-lookup"><span data-stu-id="cb7d7-134">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="cb7d7-135">Z adresy pro tento e-mailová zpráva.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-135">From address for this e-mail message.</span></span>|  
|<span data-ttu-id="cb7d7-136">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="cb7d7-136">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="cb7d7-137">Kolekce, která obsahuje příjemce této zprávy e-mailových adres.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-137">Address collection that contains the recipients of this e-mail message.</span></span>|  
|<span data-ttu-id="cb7d7-138">KOPIE</span><span class="sxs-lookup"><span data-stu-id="cb7d7-138">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="cb7d7-139">Adres kolekce, která obsahuje příjemci kopie (kopie) pro tento e-mailová zpráva.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-139">Address collection that contains the carbon copy (CC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="cb7d7-140">POLE SKRYTÁ</span><span class="sxs-lookup"><span data-stu-id="cb7d7-140">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="cb7d7-141">Kolekce adresu, která obsahuje skrytá kopie (SKRYTÁ) příjemce pro tento e-mailová zpráva.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-141">Address collection that contains the blind carbon copy (BCC) recipients for this e-mail message.</span></span>|  
|<span data-ttu-id="cb7d7-142">Tokeny</span><span class="sxs-lookup"><span data-stu-id="cb7d7-142">Tokens</span></span>|<span data-ttu-id="cb7d7-143"><xref:System.Activities.InArgument%601>< IDictionary\<řetězec, řetězec >></span><span class="sxs-lookup"><span data-stu-id="cb7d7-143"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="cb7d7-144">Tokenů pro nahrazení v textu.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-144">Tokens to replace in the body.</span></span> <span data-ttu-id="cb7d7-145">Tato funkce umožňuje uživatelům zadat některé hodnoty v textu, než můžete později nahrazuje tokeny poskytuje používání této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-145">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="cb7d7-146">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="cb7d7-146">BodyTemplateFilePath</span></span>|<span data-ttu-id="cb7d7-147">String</span><span class="sxs-lookup"><span data-stu-id="cb7d7-147">String</span></span>|<span data-ttu-id="cb7d7-148">Cesta šablonu pro text.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-148">Path of a template for the body.</span></span> <span data-ttu-id="cb7d7-149">`SendMail` Aktivity zkopíruje obsah tohoto souboru do jeho vlastnost textu.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-149">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="cb7d7-150">Šablona může obsahovat tokeny, které jsou nahrazovány obsah vlastnosti tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-150">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="cb7d7-151">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="cb7d7-151">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="cb7d7-152">Pokud je tato vlastnost nastavena, jsou všechny e-maily odeslány na adresu zadanou v ní.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-152">When this property is set, all e-mails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="cb7d7-153">Tato vlastnost je určena pro použití při testování pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-153">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="cb7d7-154">Například pokud chcete Ujistěte se, že jsou všechny e-maily odeslány bez odeslání je skutečný příjemcům.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-154">For example, when you want to make sure that all e-mails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="cb7d7-155">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="cb7d7-155">TestDropPath</span></span>|<span data-ttu-id="cb7d7-156">String</span><span class="sxs-lookup"><span data-stu-id="cb7d7-156">String</span></span>|<span data-ttu-id="cb7d7-157">Pokud je tato vlastnost nastavena, všechny e-mailů jsou také uloženy do zadaného souboru.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-157">When this property is set, all e-mails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="cb7d7-158">Tato vlastnost je určena pro použití při testování a ladění pracovních postupů, abyste měli jistotu, že formát a obsah odchozích e-mailů, je vhodné.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-158">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing e-mails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="cb7d7-159">Obsah řešení</span><span class="sxs-lookup"><span data-stu-id="cb7d7-159">Solution Contents</span></span>  
 <span data-ttu-id="cb7d7-160">Řešení obsahuje dva projekty.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-160">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="cb7d7-161">Project</span><span class="sxs-lookup"><span data-stu-id="cb7d7-161">Project</span></span>|<span data-ttu-id="cb7d7-162">Popis</span><span class="sxs-lookup"><span data-stu-id="cb7d7-162">Description</span></span>|<span data-ttu-id="cb7d7-163">Důležité soubory</span><span class="sxs-lookup"><span data-stu-id="cb7d7-163">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="cb7d7-164">SendMail</span><span class="sxs-lookup"><span data-stu-id="cb7d7-164">SendMail</span></span>|<span data-ttu-id="cb7d7-165">SendMail aktivity</span><span class="sxs-lookup"><span data-stu-id="cb7d7-165">The SendMail activity</span></span>|<span data-ttu-id="cb7d7-166">1.  SendMail.cs: implementace pro hlavní aktivitu</span><span class="sxs-lookup"><span data-stu-id="cb7d7-166">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="cb7d7-167">2.  SendMailDesigner.xaml a SendMailDesigner.xaml.cs: návrháře SendMail aktivity</span><span class="sxs-lookup"><span data-stu-id="cb7d7-167">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="cb7d7-168">3.  MailTemplateBody.htm: Šablona e-mailu mají být odeslány.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-168">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="cb7d7-169">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="cb7d7-169">SendMailTestClient</span></span>|<span data-ttu-id="cb7d7-170">Klient k testování SendMail aktivity.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-170">Client to test the SendMail activity.</span></span>  <span data-ttu-id="cb7d7-171">Tento projekt ukazuje dva způsoby vyvolání aktivity SendMail: deklarativně a programově.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-171">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="cb7d7-172">1.  Sequence1.XAML: pracovní postup, který vyvolá SendMail aktivity.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-172">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="cb7d7-173">2.  Program.cs: vyvolá Sequence1 a vytvoří také prostřednictvím kódu programu, používá SendMail pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-173">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="cb7d7-174">Další konfigurace SendMail aktivity</span><span class="sxs-lookup"><span data-stu-id="cb7d7-174">Further configuration of the SendMail activity</span></span>  
 <span data-ttu-id="cb7d7-175">I když není uvedeno v ukázce, uživatelé mohou provádět konfiguraci přidání SendMail aktivity.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-175">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="cb7d7-176">V následujících třech částech ukazují, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-176">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="cb7d7-177">E-mailu pomocí tokenů specifikovat v textu</span><span class="sxs-lookup"><span data-stu-id="cb7d7-177">Sending an email using tokens specified in the body</span></span>  
 <span data-ttu-id="cb7d7-178">Tento fragment kódu ukazuje, jak můžete odeslat e-mailu pomocí tokenů v textu.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-178">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="cb7d7-179">Všimněte si, jak jsou uvedeny tokenů v vlastnosti body.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-179">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="cb7d7-180">Hodnoty pro tyto tokeny jsou k dispozici pro vlastnost tokeny.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-180">Values for those tokens are provided to the tokens property.</span></span>  
  
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
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="cb7d7-181">E-mailu pomocí šablony</span><span class="sxs-lookup"><span data-stu-id="cb7d7-181">Sending an email using a template</span></span>  
 <span data-ttu-id="cb7d7-182">Tento fragment kódu ukazuje, jak k odesílání e-mailu pomocí šablony tokeny v textu.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-182">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="cb7d7-183">Všimněte si, že při nastavení `BodyTemplateFilePath` vlastnost není třeba zadat hodnotu pro vlastnost textu (obsah souboru šablony se zkopírují na text).</span><span class="sxs-lookup"><span data-stu-id="cb7d7-183">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
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
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="cb7d7-184">Odesílání e-mailů v režimu testování</span><span class="sxs-lookup"><span data-stu-id="cb7d7-184">Sending Mails in Testing Mode</span></span>  
 <span data-ttu-id="cb7d7-185">Tento fragment kódu ukazuje, jak nastavit dva testování vlastnosti: nastavením `TestMailTo` na všechny zprávy se budou odesílat do john.doe@contoso.con (bez ohledu na hodnoty Komu, skrytá kopie).</span><span class="sxs-lookup"><span data-stu-id="cb7d7-185">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to john.doe@contoso.con (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="cb7d7-186">Nastavením TestDropPath se taky zaznamená všechny odchozí e-mailů v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-186">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="cb7d7-187">Tyto vlastnosti můžete nastavit samostatně (nesouvisí).</span><span class="sxs-lookup"><span data-stu-id="cb7d7-187">These properties can be set independently (they are not related).</span></span>  
  
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
  
## <a name="set-up-instructions"></a><span data-ttu-id="cb7d7-188">Pokyny k instalaci</span><span class="sxs-lookup"><span data-stu-id="cb7d7-188">Set-Up Instructions</span></span>  
 <span data-ttu-id="cb7d7-189">Je vyžadován pro tato ukázka přístup k serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-189">Access to a SMTP server is required for this sample.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="cb7d7-190">nastavení serveru SMTP, naleznete na následujících odkazech.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-190"> setting up a SMTP server, see the following links.</span></span>  
  
-   [<span data-ttu-id="cb7d7-191">Webu Microsoft Technet</span><span class="sxs-lookup"><span data-stu-id="cb7d7-191">Microsoft Technet</span></span>](http://go.microsoft.com/fwlink/?LinkId=166060)  
  
-   [<span data-ttu-id="cb7d7-192">Konfigurace služby SMTP (IIS 6.0)</span><span class="sxs-lookup"><span data-stu-id="cb7d7-192">Configuring the SMTP Service (IIS 6.0)</span></span>](http://go.microsoft.com/fwlink/?LinkId=150456)  
  
-   [<span data-ttu-id="cb7d7-193">Služba IIS 7.0: Konfigurace SMTP E-Mail</span><span class="sxs-lookup"><span data-stu-id="cb7d7-193">IIS 7.0: Configure SMTP E-Mail</span></span>](http://go.microsoft.com/fwlink/?LinkId=150457)  
  
-   [<span data-ttu-id="cb7d7-194">Jak nainstalovat službu SMTP</span><span class="sxs-lookup"><span data-stu-id="cb7d7-194">How to Install the SMTP Service</span></span>](http://go.microsoft.com/fwlink/?LinkId=150458)  
  
 <span data-ttu-id="cb7d7-195">SMTP emulátorů třetích stran jsou k dispozici ke stažení.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-195">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="cb7d7-196">Chcete tuto ukázku spustit</span><span class="sxs-lookup"><span data-stu-id="cb7d7-196">To run this sample</span></span>  
  
1.  <span data-ttu-id="cb7d7-197">Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení SendMail.sln.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-197">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the SendMail.sln solution file.</span></span>  
  
2.  <span data-ttu-id="cb7d7-198">Ujistěte se, zda máte přístup k platný název serveru SMTP.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-198">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="cb7d7-199">Najdete pokyny k instalaci.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-199">See the set-up instructions.</span></span>  
  
3.  <span data-ttu-id="cb7d7-200">Konfigurace programu s touto adresou serveru a od a do e-mailové adresy.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-200">Configure the program with your server address, and From and To e-mail addresses.</span></span>  
  
     <span data-ttu-id="cb7d7-201">Pokud chcete tuto ukázku spustit správně, musíte nakonfigurovat hodnotu od a do e-mailové adresy a adresy serveru SMTP v souboru Program.cs a Sequence.xaml.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-201">To correctly run this sample, you may need to configure the value of From and To e-mail addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="cb7d7-202">Budete muset změnit adresu v obou umístěních, protože program odešle mail dvěma různými způsoby</span><span class="sxs-lookup"><span data-stu-id="cb7d7-202">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4.  <span data-ttu-id="cb7d7-203">Sestavte řešení, stiskněte CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-203">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5.  <span data-ttu-id="cb7d7-204">Chcete-li spustit řešení, stiskněte CTRL + F5.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-204">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cb7d7-205">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-205">The samples may already be installed on your machine.</span></span> <span data-ttu-id="cb7d7-206">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="cb7d7-206">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cb7d7-207">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-207">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cb7d7-208">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="cb7d7-208">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`  
  
## <a name="see-also"></a><span data-ttu-id="cb7d7-209">Viz také</span><span class="sxs-lookup"><span data-stu-id="cb7d7-209">See Also</span></span>
