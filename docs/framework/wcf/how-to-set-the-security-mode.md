---
title: 'Postupy: Nastavení režimu zabezpečení'
description: 'Naučte se, jak nastavit tři běžné režimy zabezpečení WCF u většiny předdefinovaných vazeb: přenos, zpráva a TransportWithMessageCredential.'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Mode property
- WCF, security mode
- WCF, security
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
ms.openlocfilehash: 2f834e1930b7676592f6cbc29a577424d75ebc01
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244540"
---
# <a name="how-to-set-the-security-mode"></a><span data-ttu-id="883be-103">Postupy: Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="883be-103">How to: Set the Security Mode</span></span>

<span data-ttu-id="883be-104">Zabezpečení Windows Communication Foundation (WCF) má tři běžné režimy zabezpečení, které se nacházejí u většiny předdefinovaných vazeb: přenos, zpráva a přenos s přihlašovacími údaji zprávy.</span><span class="sxs-lookup"><span data-stu-id="883be-104">Windows Communication Foundation (WCF) security has three common security modes that are found on most predefined bindings: transport, message, and "transport with message credential."</span></span> <span data-ttu-id="883be-105">Dva další režimy jsou specifické pro dvě vazby: režim "přenos pouze s přihlašovacími údaji", který se nachází v systému <xref:System.ServiceModel.BasicHttpBinding> , a režim "obojí", který se nachází v <xref:System.ServiceModel.NetMsmqBinding> .</span><span class="sxs-lookup"><span data-stu-id="883be-105">Two additional modes are specific to two bindings: the "transport-credential only" mode found on the <xref:System.ServiceModel.BasicHttpBinding>, and the "Both" mode, found on the <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="883be-106">Toto téma se však zaměřuje na tři běžné režimy zabezpečení:, a <xref:System.ServiceModel.SecurityMode.Transport> <xref:System.ServiceModel.SecurityMode.Message> <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential> .</span><span class="sxs-lookup"><span data-stu-id="883be-106">However, this topic concentrates on the three common security modes: <xref:System.ServiceModel.SecurityMode.Transport>, <xref:System.ServiceModel.SecurityMode.Message>, and <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>

<span data-ttu-id="883be-107">Všimněte si, že ne každá předdefinovaná vazba podporuje všechny tyto režimy.</span><span class="sxs-lookup"><span data-stu-id="883be-107">Note that not every predefined binding supports all of these modes.</span></span> <span data-ttu-id="883be-108">Toto téma nastaví režim s <xref:System.ServiceModel.WSHttpBinding> <xref:System.ServiceModel.NetTcpBinding> třídami a a ukazuje, jak nastavit režim programově i prostřednictvím konfigurace.</span><span class="sxs-lookup"><span data-stu-id="883be-108">This topic sets the mode with the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> classes and demonstrates how to set the mode both programmatically and through configuration.</span></span>

<span data-ttu-id="883be-109">Další informace najdete v tématu zabezpečení služby WCF, [Přehled zabezpečení](./feature-details/security-overview.md), zabezpečení [služeb](securing-services.md) [a zabezpečení služeb a klientů](./feature-details/securing-services-and-clients.md).</span><span class="sxs-lookup"><span data-stu-id="883be-109">For more information, see WCF security, see [Security Overview](./feature-details/security-overview.md), [Securing Services](securing-services.md), and [Securing Services and Clients](./feature-details/securing-services-and-clients.md).</span></span> <span data-ttu-id="883be-110">Další informace o režimu přenosu a zprávě najdete v tématu [zabezpečení přenosu](./feature-details/transport-security.md) a [zabezpečení zpráv](./feature-details/message-security-in-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="883be-110">For more information about transport mode and message, see [Transport Security](./feature-details/transport-security.md) and [Message Security](./feature-details/message-security-in-wcf.md).</span></span>

## <a name="to-set-the-security-mode-in-code"></a><span data-ttu-id="883be-111">Nastavení režimu zabezpečení v kódu</span><span class="sxs-lookup"><span data-stu-id="883be-111">To set the security mode in code</span></span>

1. <span data-ttu-id="883be-112">Vytvořte instanci třídy vazby, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="883be-112">Create an instance of the binding class that you are using.</span></span> <span data-ttu-id="883be-113">Seznam předdefinovaných vazeb najdete v tématu [vazby poskytované systémem](system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="883be-113">For a list of predefined bindings, see [System-Provided Bindings](system-provided-bindings.md).</span></span> <span data-ttu-id="883be-114">Tento příklad vytvoří instanci <xref:System.ServiceModel.WSHttpBinding> třídy.</span><span class="sxs-lookup"><span data-stu-id="883be-114">This example creates an instance of the <xref:System.ServiceModel.WSHttpBinding> class.</span></span>

2. <span data-ttu-id="883be-115">Nastavte `Mode` vlastnost objektu vráceného `Security` vlastností.</span><span class="sxs-lookup"><span data-stu-id="883be-115">Set the `Mode` property of the object returned by the `Security` property.</span></span>

     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]

     <span data-ttu-id="883be-116">Případně můžete nastavit režim na zprávu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="883be-116">Alternatively, set the mode to message, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]

     <span data-ttu-id="883be-117">Nebo nastavte režim pro přenos s přihlašovacími údaji zprávy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="883be-117">Or set the mode to transport with message credentials, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]

3. <span data-ttu-id="883be-118">Můžete také nastavit režim v konstruktoru vazby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="883be-118">You can also set the mode in the constructor of the binding, as shown in the following code.</span></span>

     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]

## <a name="setting-the-clientcredentialtype-property"></a><span data-ttu-id="883be-119">Nastavení vlastnosti ClientCredentialType</span><span class="sxs-lookup"><span data-stu-id="883be-119">Setting the ClientCredentialType Property</span></span>

<span data-ttu-id="883be-120">Nastavení režimu na jednu ze tří hodnot určuje způsob, jakým se nastavuje `ClientCredentialType` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="883be-120">Setting the mode to one of the three values determines how you set the `ClientCredentialType` property.</span></span> <span data-ttu-id="883be-121">Například použití <xref:System.ServiceModel.WSHttpBinding> třídy, nastavení režimu na `Transport` znamená, že musíte nastavit <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> vlastnost <xref:System.ServiceModel.HttpTransportSecurity> třídy na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="883be-121">For example, using the <xref:System.ServiceModel.WSHttpBinding> class, setting the mode to `Transport` means you must set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property of the <xref:System.ServiceModel.HttpTransportSecurity> class to an appropriate value.</span></span>

### <a name="to-set-the-clientcredentialtype-property-for-transport-mode"></a><span data-ttu-id="883be-122">Nastavení vlastnosti ClientCredentialType pro transportní režim</span><span class="sxs-lookup"><span data-stu-id="883be-122">To set the ClientCredentialType property for Transport mode</span></span>

1. <span data-ttu-id="883be-123">Vytvořte instanci vazby.</span><span class="sxs-lookup"><span data-stu-id="883be-123">Create an instance of the binding.</span></span>

2. <span data-ttu-id="883be-124">Nastavte `Mode` vlastnost na hodnotu `Transport` .</span><span class="sxs-lookup"><span data-stu-id="883be-124">Set the `Mode` property to `Transport`.</span></span>

3. <span data-ttu-id="883be-125">Nastavte `ClientCredential` vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="883be-125">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="883be-126">Následující kód nastaví vlastnost na hodnotu `Windows` .</span><span class="sxs-lookup"><span data-stu-id="883be-126">The following code sets the property to `Windows`.</span></span>

     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]

### <a name="to-set-the-clientcredentialtype-property-for-message-mode"></a><span data-ttu-id="883be-127">Nastavení vlastnosti ClientCredentialType pro režim zprávy</span><span class="sxs-lookup"><span data-stu-id="883be-127">To set the ClientCredentialType property for Message mode</span></span>

1. <span data-ttu-id="883be-128">Vytvořte instanci vazby.</span><span class="sxs-lookup"><span data-stu-id="883be-128">Create an instance of the binding.</span></span>

2. <span data-ttu-id="883be-129">Nastavte `Mode` vlastnost na hodnotu `Message` .</span><span class="sxs-lookup"><span data-stu-id="883be-129">Set the `Mode` property to `Message`.</span></span>

3. <span data-ttu-id="883be-130">Nastavte `ClientCredential` vlastnost na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="883be-130">Set the `ClientCredential` property to an appropriate value.</span></span> <span data-ttu-id="883be-131">Následující kód nastaví vlastnost na hodnotu `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="883be-131">The following code sets the property to `Certificate`.</span></span>

     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]

### <a name="to-set-the-mode-and-clientcredentialtype-property-in-configuration"></a><span data-ttu-id="883be-132">Nastavení vlastnosti Mode a ClientCredentialType v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="883be-132">To set the Mode and ClientCredentialType property in configuration</span></span>

1. <span data-ttu-id="883be-133">Přidejte vhodný element vazby do [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="883be-133">Add an appropriate binding element to the [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="883be-134">Následující příklad přidá [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) prvek.</span><span class="sxs-lookup"><span data-stu-id="883be-134">The following example adds a [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

2. <span data-ttu-id="883be-135">Přidejte `<binding>` element a nastavte jeho `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="883be-135">Add a `<binding>` element and set its `name` attribute to an appropriate value.</span></span>

3. <span data-ttu-id="883be-136">Přidejte `<security>` element a nastavte `mode` atribut na `Message` , `Transport` , nebo `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="883be-136">Add a `<security>` element and set the `mode` attribute to `Message`, `Transport`, or `TransportWithMessageCredential`.</span></span>

4. <span data-ttu-id="883be-137">Pokud je režim nastaven na `Transport` , přidejte `<transport>` element a nastavte `clientCredential` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="883be-137">If the mode is set to `Transport`, add a `<transport>` element and set the `clientCredential` attribute to an appropriate value.</span></span>

     <span data-ttu-id="883be-138">Následující příklad nastaví režim na " `Transport"` a poté nastaví `clientCredentialType` atribut `<transport>` elementu na" `Windows"` .</span><span class="sxs-lookup"><span data-stu-id="883be-138">The following example sets the mode to "`Transport"`, and then sets the `clientCredentialType` attribute of the `<transport>` element to "`Windows"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="TransportSecurity">
        <security mode="Transport" >
           <transport clientCredentialType = "Windows" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="883be-139">Případně nastavte na `security mode` "" `Message"` , následované `<"message">` prvkem.</span><span class="sxs-lookup"><span data-stu-id="883be-139">Alternatively, set the `security mode` to "`Message"`, followed by a `<"message">` element.</span></span> <span data-ttu-id="883be-140">V tomto příkladu se nastaví `clientCredentialType` na `Certificate"` .</span><span class="sxs-lookup"><span data-stu-id="883be-140">This example sets the `clientCredentialType` to "`Certificate"`.</span></span>

    ```xml
    <wsHttpBinding>
    <binding name="MessageSecurity">
        <security mode="Message" >
           <message clientCredentialType = "Certificate" />
        </security>
    </binding>
    </wsHttpBinding >
    ```

     <span data-ttu-id="883be-141">Použití <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> hodnoty je zvláštní případ a je vysvětleno níže.</span><span class="sxs-lookup"><span data-stu-id="883be-141">Using the <xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential> value is a special case, and is explained below.</span></span>

### <a name="using-transportwithmessagecredential"></a><span data-ttu-id="883be-142">Použití TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="883be-142">Using TransportWithMessageCredential</span></span>

<span data-ttu-id="883be-143">Při nastavení režimu zabezpečení na `TransportWithMessageCredential` je přenos určena skutečným mechanismem, který poskytuje zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="883be-143">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="883be-144">Protokol HTTP například používá SSL (Secure Sockets Layer) (SSL) přes protokol HTTP (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="883be-144">For example, the HTTP protocol uses Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="883be-145">Proto `ClientCredentialType` se nastavení vlastnosti libovolného objektu zabezpečení přenosu (například <xref:System.ServiceModel.HttpTransportSecurity> ) ignoruje.</span><span class="sxs-lookup"><span data-stu-id="883be-145">Therefore, setting the `ClientCredentialType` property of any transport security object (such as <xref:System.ServiceModel.HttpTransportSecurity>) is ignored.</span></span>  <span data-ttu-id="883be-146">Jinými slovy můžete nastavit pouze `ClientCredentialType` objekt zabezpečení zprávy (pro `WSHttpBinding` vazbu, <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> objekt).</span><span class="sxs-lookup"><span data-stu-id="883be-146">In other words, you can only set the `ClientCredentialType` of the message security object (for the `WSHttpBinding` binding, the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> object).</span></span>

<span data-ttu-id="883be-147">Další informace najdete v tématu [Postupy: použití zabezpečení přenosu a přihlašovacích údajů pro zprávy](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span><span class="sxs-lookup"><span data-stu-id="883be-147">For more information, see [How to: Use Transport Security and Message Credentials](./feature-details/how-to-use-transport-security-and-message-credentials.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="883be-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="883be-148">See also</span></span>

- [<span data-ttu-id="883be-149">Postupy: Konfigurace portu s certifikátem SSL</span><span class="sxs-lookup"><span data-stu-id="883be-149">How to: Configure a Port with an SSL Certificate</span></span>](./feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [<span data-ttu-id="883be-150">Postupy: Použití přihlašovacích údajů k zabezpečení přenosů a zpráv</span><span class="sxs-lookup"><span data-stu-id="883be-150">How to: Use Transport Security and Message Credentials</span></span>](./feature-details/how-to-use-transport-security-and-message-credentials.md)
- [<span data-ttu-id="883be-151">Zabezpečení přenosu</span><span class="sxs-lookup"><span data-stu-id="883be-151">Transport Security</span></span>](./feature-details/transport-security.md)
- [<span data-ttu-id="883be-152">Zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="883be-152">Message Security</span></span>](./feature-details/message-security-in-wcf.md)
- [<span data-ttu-id="883be-153">Přehled zabezpečení</span><span class="sxs-lookup"><span data-stu-id="883be-153">Security Overview</span></span>](./feature-details/security-overview.md)
- [<span data-ttu-id="883be-154">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="883be-154">System-Provided Bindings</span></span>](system-provided-bindings.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-wshttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-basichttpbinding.md)
- [\<security>](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
