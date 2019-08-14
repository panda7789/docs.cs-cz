---
title: 'Postupy: Nastavení režimu zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 6bd81bd24d28f0a9e318d60a3b7fb4aa059f9a49
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971979"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="e8cd8-102">Postupy: Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e8cd8-102">How to: Set the Security Mode</span></span>

<span data-ttu-id="e8cd8-103">Zabezpečení Windows Communication Foundation (WCF) má tři běžné režimy zabezpečení, které se nacházejí u většiny předdefinovaných vazeb: přenos, zpráva a přenos s přihlašovacími údaji zprávy.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="e8cd8-104">Dva další režimy jsou specifické pro dvě vazby: režim "přenos pouze s přihlašovacími údaji" <xref:System.ServiceModel.BasicHttpBinding>, který se nachází v systému, a režim "obojí", který se nachází <xref:System.ServiceModel.NetMsmqBinding>v.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="e8cd8-105">Toto téma se však zaměřuje na tři běžné režimy zabezpečení: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message> <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>a.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="e8cd8-106">Všimněte si, že ne každá předdefinovaná vazba podporuje všechny tyto režimy.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="e8cd8-107">Toto téma nastaví režim s <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> třídami a a ukazuje, jak nastavit režim programově i prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="e8cd8-108">Další informace najdete v tématu zabezpečení služby WCF, [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md), zabezpečení [služeb](../../../docs/framework/wcf/securing-services.md) [a zabezpečení služeb a klientů](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="e8cd8-108">For more information, see WCF security, see [Security Overview](../../../docs/framework/wcf/feature-details/security-overview.md), [Securing Services](../../../docs/framework/wcf/securing-services.md), and [Securing Services and Clients](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="e8cd8-109">Další informace o režimu přenosu a zprávě najdete v tématu [zabezpečení přenosu](../../../docs/framework/wcf/feature-details/transport-security.md) a [zabezpečení zpráv](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="e8cd8-109">For more information about transport mode and message, see [Transport Security](../../../docs/framework/wcf/feature-details/transport-security.md) and [Message Security](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="e8cd8-110">Nastavení režimu zabezpečení v kódu</span><span class="sxs-lookup"><span data-stu-id="e8cd8-110">To set the security mode in code</span></span>

1. <span data-ttu-id="e8cd8-111">Vytvořte instanci třídy vazby, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="e8cd8-112">Seznam předdefinovaných vazeb najdete v tématu [vazby poskytované systémem](../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="e8cd8-112">For a list of predefined bindings, see [System-Provided Bindings](../../../docs/framework/wcf/system-provided-bindings.md).</span></span> <span data-ttu-id="e8cd8-113">Tento příklad vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="e8cd8-114">Nastavte vlastnost objektu vráceného `Security`vlastností. `Mode`</span><span class="sxs-lookup"><span data-stu-id="e8cd8-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="e8cd8-115">Případně můžete nastavit režim na zprávu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-115">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="e8cd8-116">Nebo nastavte režim pro přenos s přihlašovacími údaji zprávy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="e8cd8-117">Můžete také nastavit režim v konstruktoru vazby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="e8cd8-118">Nastavení vlastnosti ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="e8cd8-118">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="e8cd8-119">Nastavení režimu na jednu ze tří hodnot určuje způsob, jakým se nastavuje `ClientCredentialType` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="e8cd8-120">Například použití <xref:System.ServiceModel.WSHttpBinding> třídy, nastavení režimu na `Transport` <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> znamená, že musíte <xref:System.ServiceModel.HttpTransportSecurity> nastavit vlastnost třídy na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="e8cd8-121">Nastavení vlastnosti ClientCredentialType pro transportní režim</span><span class="sxs-lookup"><span data-stu-id="e8cd8-121">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="e8cd8-122">Vytvořte instanci vazby.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-122">Create an instance of the binding.</span></span>

2. <span data-ttu-id="e8cd8-123">Nastavte `Mode` vlastnost `Transport`.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-123">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="e8cd8-124">`ClientCredential` Nastavte vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="e8cd8-125">Následující kód nastaví vlastnost na `Windows`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-125">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="e8cd8-126">Nastavení vlastnosti ClientCredentialType pro režim zprávy</span><span class="sxs-lookup"><span data-stu-id="e8cd8-126">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="e8cd8-127">Vytvořte instanci vazby.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-127">Create an instance of the binding.</span></span>

2. <span data-ttu-id="e8cd8-128">Nastavte `Mode` vlastnost `Message`.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-128">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="e8cd8-129">`ClientCredential` Nastavte vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="e8cd8-130">Následující kód nastaví vlastnost na `Certificate`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-130">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="e8cd8-131">Nastavení vlastnosti Mode a ClientCredentialType v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="e8cd8-131">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="e8cd8-132">Přidejte příslušný prvek vazby do [ \<prvku > vazby](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-132">Add an appropriate binding element to the [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="e8cd8-133">Následující příklad přidá [ \<prvek WSHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="e8cd8-133">The following example adds a [\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="e8cd8-134">Přidejte element a nastavte jeho `name` atribut na odpovídající hodnotu. `<binding>`</span><span class="sxs-lookup"><span data-stu-id="e8cd8-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="e8cd8-135">`mode` `Message`Přidejte element a nastavte atribut na, `Transport`, nebo `TransportWithMessageCredential`. `<security>`</span><span class="sxs-lookup"><span data-stu-id="e8cd8-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="e8cd8-136">Pokud je režim nastaven na `Transport`, `<transport>` přidejte element a nastavte `clientCredential` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="e8cd8-137">Následující příklad nastaví`Transport"`režim na "a poté `clientCredentialType` nastaví atribut `<transport>` elementu na"`Windows"`.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="e8cd8-138">Případně nastavte `security mode` na ""`Message"`, následované `<"message">` prvkem.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="e8cd8-139">V `clientCredentialType` tomto příkladu se nastaví`Certificate"`na.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="e8cd8-140"><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> Použití hodnoty je zvláštní případ a je vysvětleno níže.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="e8cd8-141">Použití TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="e8cd8-141">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="e8cd8-142">Při nastavení režimu zabezpečení na `TransportWithMessageCredential`je přenos určena skutečným mechanismem, který poskytuje zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="e8cd8-143">Protokol HTTP například používá SSL (Secure Sockets Layer) (SSL) přes protokol HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="e8cd8-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="e8cd8-144">Proto se nastavení `ClientCredentialType` vlastnosti libovolného objektu zabezpečení přenosu ( <xref:System.ServiceModel.HttpTransportSecurity>například) ignoruje.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="e8cd8-145">Jinými slovy můžete nastavit `ClientCredentialType` pouze objekt zabezpečení zprávy ( `WSHttpBinding` pro vazbu, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> objekt).</span><span class="sxs-lookup"><span data-stu-id="e8cd8-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="e8cd8-146">Další informace najdete v tématu [jak: Použijte zabezpečení přenosu a přihlašovací údaje](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="e8cd8-146">For more information, see [How to: Use Transport Security and Message Credentials](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e8cd8-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8cd8-147">See also</span></span>

- [<span data-ttu-id="e8cd8-148">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="e8cd8-148">How to: Configure a Port with an SSL Certificate</span></span>](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="e8cd8-149">Postupy: Použít zabezpečení přenosu a přihlašovací údaje pro zprávy</span><span class="sxs-lookup"><span data-stu-id="e8cd8-149">How to: Use Transport Security and Message Credentials</span></span>](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="e8cd8-150">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="e8cd8-150">Transport Security</span></span>](../../../docs/framework/wcf/feature-details/transport-security.md)
- [<span data-ttu-id="e8cd8-151">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="e8cd8-151">Message Security</span></span>](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="e8cd8-152">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e8cd8-152">Security Overview</span></span>](../../../docs/framework/wcf/feature-details/security-overview.md)
- [<span data-ttu-id="e8cd8-153">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="e8cd8-153">System-Provided Bindings</span></span>](../../../docs/framework/wcf/system-provided-bindings.md)
- [<span data-ttu-id="e8cd8-154">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e8cd8-154">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [<span data-ttu-id="e8cd8-155">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e8cd8-155">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [<span data-ttu-id="e8cd8-156">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e8cd8-156">\<security></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
