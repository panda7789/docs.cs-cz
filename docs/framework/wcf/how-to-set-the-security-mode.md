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
ms.openlocfilehash: 9b9e25cbafb6387b4584a21fd642d80bc41cd8dc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320899"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="4e1ef-102">Postupy: Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4e1ef-102">How to: Set the Security Mode</span></span>

<span data-ttu-id="4e1ef-103">Zabezpečení Windows Communication Foundation (WCF) má tři běžné režimy zabezpečení, které se nacházejí u většiny předdefinovaných vazeb: přenos, zpráva a přenos s přihlašovacími údaji zprávy.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-103">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="4e1ef-104">Dva další režimy jsou specifické pro dvě vazby: režim "přenos – pouze přihlašovací údaje", který se nachází na <xref:System.ServiceModel.BasicHttpBinding>, a režim "obojí", který se nachází v <xref:System.ServiceModel.NetMsmqBinding>.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-104">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="4e1ef-105">Toto téma se však zaměřuje na tři běžné režimy zabezpečení: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>a <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-105">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="4e1ef-106">Všimněte si, že ne každá předdefinovaná vazba podporuje všechny tyto režimy.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-106">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="4e1ef-107">Toto téma nastaví režim pomocí tříd <xref:System.ServiceModel.WSHttpBinding> a <xref:System.ServiceModel.NetTcpBinding> a ukazuje, jak nastavit režim programově i prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-107">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="4e1ef-108">Další informace najdete v tématu zabezpečení služby WCF, [Přehled zabezpečení](./feature-details/security-overview.md), zabezpečení [služeb](securing-services.md) [a zabezpečení služeb a klientů](./feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="4e1ef-108">For more information, see WCF security, see [Security Overview](./feature-details/security-overview.md), [Securing Services](securing-services.md), and [Securing Services and Clients](./feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="4e1ef-109">Další informace o režimu přenosu a zprávě najdete v tématu [zabezpečení přenosu](./feature-details/transport-security.md) a [zabezpečení zpráv](./feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="4e1ef-109">For more information about transport mode and message, see [Transport Security](./feature-details/transport-security.md) and [Message Security](./feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="4e1ef-110">Nastavení režimu zabezpečení v kódu</span><span class="sxs-lookup"><span data-stu-id="4e1ef-110">To set the security mode in code</span></span>

1. <span data-ttu-id="4e1ef-111">Vytvořte instanci třídy vazby, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-111">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="4e1ef-112">Seznam předdefinovaných vazeb najdete v tématu [vazby poskytované systémem](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="4e1ef-112">For a list of predefined bindings, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="4e1ef-113">Tento příklad vytvoří instanci třídy <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-113">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="4e1ef-114">Nastavte vlastnost `Mode` objektu vráceného vlastností `Security`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-114">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="4e1ef-115">Případně můžete nastavit režim na zprávu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-115">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="4e1ef-116">Nebo nastavte režim pro přenos s přihlašovacími údaji zprávy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-116">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="4e1ef-117">Můžete také nastavit režim v konstruktoru vazby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-117">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="4e1ef-118">Nastavení vlastnosti ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="4e1ef-118">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="4e1ef-119">Nastavení režimu na jednu ze tří hodnot určuje způsob, jakým se nastavuje vlastnost `ClientCredentialType`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-119">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="4e1ef-120">Například použití třídy <xref:System.ServiceModel.WSHttpBinding>, nastavení režimu pro `Transport` znamená, že je nutné nastavit vlastnost <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> třídy <xref:System.ServiceModel.HttpTransportSecurity> na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-120">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="4e1ef-121">Nastavení vlastnosti ClientCredentialType pro transportní režim</span><span class="sxs-lookup"><span data-stu-id="4e1ef-121">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="4e1ef-122">Vytvořte instanci vazby.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-122">Create an instance of the binding.</span></span>

2. <span data-ttu-id="4e1ef-123">Nastavte `Mode` vlastnost `Transport`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-123">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="4e1ef-124">Vlastnost `ClientCredential` nastavte na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-124">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="4e1ef-125">Následující kód nastaví vlastnost na hodnotu `Windows`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-125">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="4e1ef-126">Nastavení vlastnosti ClientCredentialType pro režim zprávy</span><span class="sxs-lookup"><span data-stu-id="4e1ef-126">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="4e1ef-127">Vytvořte instanci vazby.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-127">Create an instance of the binding.</span></span>

2. <span data-ttu-id="4e1ef-128">Nastavte `Mode` vlastnost `Message`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-128">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="4e1ef-129">Vlastnost `ClientCredential` nastavte na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-129">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="4e1ef-130">Následující kód nastaví vlastnost na hodnotu `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-130">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="4e1ef-131">Nastavení vlastnosti Mode a ClientCredentialType v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="4e1ef-131">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="4e1ef-132">Přidejte vhodný element vazby do [\<vazeb >](../configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-132">Add an appropriate binding element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="4e1ef-133">Následující příklad přidá prvek [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="4e1ef-133">The following example adds a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="4e1ef-134">Přidejte prvek `<binding>` a nastavte jeho atribut `name` na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-134">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="4e1ef-135">Přidejte prvek `<security>` a nastavte atribut `mode` na `Message`, `Transport`nebo `TransportWithMessageCredential`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-135">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="4e1ef-136">Pokud je režim nastaven na `Transport`, přidejte prvek `<transport>` a nastavte atribut `clientCredential` na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-136">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="4e1ef-137">Následující příklad nastaví režim na "`Transport"`a poté nastaví atribut `clientCredentialType` elementu `<transport>` na hodnotu"`Windows"`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-137">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="4e1ef-138">Případně nastavte `security mode` na "`Message"`" následovaný elementem `<"message">`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-138">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="4e1ef-139">V tomto příkladu se nastaví `clientCredentialType` na "`Certificate"`.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-139">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="4e1ef-140">Použití hodnoty <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> je zvláštní případ a je vysvětleno níže.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-140">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="4e1ef-141">Použití TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="4e1ef-141">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="4e1ef-142">Když nastavíte režim zabezpečení na `TransportWithMessageCredential`, Transport určí skutečný mechanismus, který poskytuje zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-142">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="4e1ef-143">Protokol HTTP například používá SSL (Secure Sockets Layer) (SSL) přes protokol HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="4e1ef-143">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="4e1ef-144">Proto se nastavení vlastnosti `ClientCredentialType` libovolného objektu zabezpečení přenosu (například <xref:System.ServiceModel.HttpTransportSecurity>) ignoruje.</span><span class="sxs-lookup"><span data-stu-id="4e1ef-144">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="4e1ef-145">Jinými slovy můžete nastavit pouze `ClientCredentialType` objektu zabezpečení zprávy (pro vazbu `WSHttpBinding`, objekt <xref:System.ServiceModel.NonDualMessageSecurityOverHttp>).</span><span class="sxs-lookup"><span data-stu-id="4e1ef-145">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="4e1ef-146">Další informace najdete v tématu [Postupy: použití zabezpečení přenosu a přihlašovacích údajů pro zprávy](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="4e1ef-146">For more information, see [How to: Use Transport Security and Message Credentials](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e1ef-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4e1ef-147">See also</span></span>

- [<span data-ttu-id="4e1ef-148">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="4e1ef-148">How to: Configure a Port with an SSL Certificate</span></span>](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="4e1ef-149">Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv</span><span class="sxs-lookup"><span data-stu-id="4e1ef-149">How to: Use Transport Security and Message Credentials</span></span>](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="4e1ef-150">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="4e1ef-150">Transport Security</span></span>](./feature-details/transport-security.md)
- [<span data-ttu-id="4e1ef-151">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="4e1ef-151">Message Security</span></span>](./feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="4e1ef-152">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4e1ef-152">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="4e1ef-153">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="4e1ef-153">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [<span data-ttu-id="4e1ef-154">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="4e1ef-154">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [<span data-ttu-id="4e1ef-155">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="4e1ef-155">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [<span data-ttu-id="4e1ef-156">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="4e1ef-156">\<security></span></span>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
