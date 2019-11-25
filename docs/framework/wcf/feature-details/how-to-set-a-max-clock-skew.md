---
title: 'Postupy: nastavení maximálního zešikmení času'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- MaxClockSkew property
- WCF, custom bindings
ms.assetid: 491d1705-eb29-43c2-a44c-c0cf996f74eb
ms.openlocfilehash: 96afa61d32e1ba744c9f3dbbeeb7fb2e55157f4c
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141656"
---
# <a name="how-to-set-a-max-clock-skew"></a><span data-ttu-id="86d23-102">Postupy: nastavení maximálního zešikmení času</span><span class="sxs-lookup"><span data-stu-id="86d23-102">How to: Set a Max Clock Skew</span></span>
<span data-ttu-id="86d23-103">V případě, že se nastavení hodin ve dvou počítačích liší, je možné časově kritické funkce dekolejnice.</span><span class="sxs-lookup"><span data-stu-id="86d23-103">Time-critical functions can be derailed if the clock settings on two computers are different.</span></span> <span data-ttu-id="86d23-104">Pro zmírnění této možnosti můžete nastavit vlastnost `MaxClockSkew` na <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="86d23-104">To mitigate this possibility, you can set the `MaxClockSkew` property to a <xref:System.TimeSpan>.</span></span> <span data-ttu-id="86d23-105">Tato vlastnost je k dispozici na dvou třídách:</span><span class="sxs-lookup"><span data-stu-id="86d23-105">This property is available on two classes:</span></span>  
  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
  
> [!IMPORTANT]
> <span data-ttu-id="86d23-106">V případě zabezpečené konverzace se musí při spuštění služby nebo klienta provést změny vlastnosti `MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="86d23-106">For a secure conversation, changes to the `MaxClockSkew` property  must be made when the service or client is bootstrapped.</span></span> <span data-ttu-id="86d23-107">Chcete-li to provést, musíte nastavit vlastnost u <xref:System.ServiceModel.Channels.SecurityBindingElement> vráceného vlastností <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86d23-107">To do this, you must set the property on the <xref:System.ServiceModel.Channels.SecurityBindingElement> returned by the <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters.BootstrapSecurityBindingElement%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="86d23-108">Chcete-li změnit vlastnost u jedné z vazeb poskytovaných systémem, je nutné najít prvek vazby zabezpečení v kolekci vazeb a nastavit vlastnost `MaxClockSkew` na novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="86d23-108">To change the property on one of the system-provided bindings, you must find the security binding element in the collection of bindings and set the `MaxClockSkew` property to a new value.</span></span> <span data-ttu-id="86d23-109">Dvě třídy jsou odvozeny od <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="86d23-109">Two classes derive from the <xref:System.ServiceModel.Channels.SecurityBindingElement>: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="86d23-110">Při načítání vazby zabezpečení z kolekce je třeba přetypovat na jeden z těchto typů, aby bylo možné správně nastavit vlastnost `MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="86d23-110">When retrieving the security binding from the collection, you must cast to one of these types in order to correctly set the `MaxClockSkew` property.</span></span> <span data-ttu-id="86d23-111">Následující příklad používá <xref:System.ServiceModel.WSHttpBinding>, který používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="86d23-111">The following example uses a <xref:System.ServiceModel.WSHttpBinding>, which uses the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="86d23-112">Seznam, který určuje typ vazby zabezpečení, který se má použít v každé vazbě poskytované systémem, najdete v tématu [vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="86d23-112">For a list that specifies which type of security binding to use in each system-provided binding, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="to-create-a-custom-binding-with-a-new-clock-skew-value-in-code"></a><span data-ttu-id="86d23-113">Vytvoření vlastní vazby s novou hodnotou asymetrie hodin v kódu</span><span class="sxs-lookup"><span data-stu-id="86d23-113">To create a custom binding with a new clock skew value in code</span></span>  
  
> [!WARNING]
> <span data-ttu-id="86d23-114">Do kódu přidejte odkazy na následující obory názvů: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>a <xref:System.ServiceModel.Security.Tokens>.</span><span class="sxs-lookup"><span data-stu-id="86d23-114">Add references to the following namespaces in your code: <xref:System.ServiceModel.Channels>, <xref:System.ServiceModel.Description>, <xref:System.Security.Permissions>, and <xref:System.ServiceModel.Security.Tokens>.</span></span>  
  
1. <span data-ttu-id="86d23-115">Vytvořte instanci třídy <xref:System.ServiceModel.WSHttpBinding> a nastavte její režim zabezpečení na <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86d23-115">Create an instance of a <xref:System.ServiceModel.WSHttpBinding> class and set its security mode to <xref:System.ServiceModel.SecurityMode.Message?displayProperty=nameWithType>.</span></span>  
  
2. <span data-ttu-id="86d23-116">Vytvořte novou instanci třídy <xref:System.ServiceModel.Channels.BindingElementCollection> voláním metody <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A>.</span><span class="sxs-lookup"><span data-stu-id="86d23-116">Create a new instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class by calling the <xref:System.ServiceModel.WSHttpBinding.CreateBindingElements%2A> method.</span></span>  
  
3. <span data-ttu-id="86d23-117">K nalezení elementu vazby zabezpečení použijte metodu <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> třídy <xref:System.ServiceModel.Channels.BindingElementCollection>.</span><span class="sxs-lookup"><span data-stu-id="86d23-117">Use the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method of the <xref:System.ServiceModel.Channels.BindingElementCollection> class to find the security binding element.</span></span>  
  
4. <span data-ttu-id="86d23-118">Při použití metody <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> přetypování na skutečný typ.</span><span class="sxs-lookup"><span data-stu-id="86d23-118">When using the <xref:System.ServiceModel.Channels.BindingElementCollection.Find%2A> method, cast to the actual type.</span></span> <span data-ttu-id="86d23-119">Níže uvedený příklad přetypování na typ <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="86d23-119">The example below casts to the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> type.</span></span>  
  
5. <span data-ttu-id="86d23-120">Nastavte vlastnost <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> v elementu vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="86d23-120">Set the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> property on the security binding element.</span></span>  
  
6. <span data-ttu-id="86d23-121">Vytvořte <xref:System.ServiceModel.ServiceHost> s příslušným typem služby a základní adresou.</span><span class="sxs-lookup"><span data-stu-id="86d23-121">Create a <xref:System.ServiceModel.ServiceHost> with an appropriate service type and base address.</span></span>  
  
7. <span data-ttu-id="86d23-122">Použijte metodu <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> pro přidání koncového bodu a zahrnutí <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="86d23-122">Use the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method to add an endpoint and include the <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
     [!code-csharp[c_MaxClockSkew#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_maxclockskew/cs/source.cs#1)]
     [!code-vb[c_MaxClockSkew#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_maxclockskew/vb/source.vb#1)]  
  
## <a name="to-set-the-maxclockskew-in-configuration"></a><span data-ttu-id="86d23-123">Nastavení MaxClockSkew v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="86d23-123">To set the MaxClockSkew in configuration</span></span>  
  
1. <span data-ttu-id="86d23-124">Vytvořte [\<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) v části [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="86d23-124">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) in the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element section.</span></span>  
  
2. <span data-ttu-id="86d23-125">Vytvořte [\<vazbu >](../../configure-apps/file-schema/wcf/bindings.md) elementu a nastavte atribut `name` na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="86d23-125">Create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="86d23-126">Následující příklad nastaví `MaxClockSkewBinding`.</span><span class="sxs-lookup"><span data-stu-id="86d23-126">The following example sets it to `MaxClockSkewBinding`.</span></span>  
  
3. <span data-ttu-id="86d23-127">Přidejte element Encoding.</span><span class="sxs-lookup"><span data-stu-id="86d23-127">Add an encoding element.</span></span> <span data-ttu-id="86d23-128">Následující příklad přidá [\<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span><span class="sxs-lookup"><span data-stu-id="86d23-128">The example below adds a [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
4. <span data-ttu-id="86d23-129">Přidejte prvek [> zabezpečení\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) a nastavte atribut `authenticationMode` na příslušné nastavení.</span><span class="sxs-lookup"><span data-stu-id="86d23-129">Add a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element and set the `authenticationMode` attribute to an appropriate setting.</span></span> <span data-ttu-id="86d23-130">Následující příklad nastaví atribut tak, aby `Kerberos` určit, že služba používá ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="86d23-130">The following example set the attribute to `Kerberos` to specify that the service use Windows authentication.</span></span>  
  
5. <span data-ttu-id="86d23-131">Přidejte [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte atribut `maxClockSkew` na hodnotu ve formě `"##:##:##"`.</span><span class="sxs-lookup"><span data-stu-id="86d23-131">Add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to a value in the form of `"##:##:##"`.</span></span> <span data-ttu-id="86d23-132">V následujícím příkladu se nastaví na 7 minut.</span><span class="sxs-lookup"><span data-stu-id="86d23-132">The following example sets it to 7 minutes.</span></span> <span data-ttu-id="86d23-133">Volitelně přidejte [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) a nastavte atribut `maxClockSkew` na příslušné nastavení.</span><span class="sxs-lookup"><span data-stu-id="86d23-133">Optionally, add a [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md) and set the `maxClockSkew` attribute to an appropriate setting.</span></span>  
  
6. <span data-ttu-id="86d23-134">Přidejte transportní element.</span><span class="sxs-lookup"><span data-stu-id="86d23-134">Add a transport element.</span></span> <span data-ttu-id="86d23-135">Následující příklad používá [\<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span><span class="sxs-lookup"><span data-stu-id="86d23-135">The following example uses an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
7. <span data-ttu-id="86d23-136">Pro zabezpečenou konverzaci musí být nastavení zabezpečení provedeno při spuštění v prvku [\<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) .</span><span class="sxs-lookup"><span data-stu-id="86d23-136">For a secure conversation, the security settings must occur at the bootstrap in the [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element.</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="MaxClockSkewBinding">  
            <textMessageEncoding />  
            <security authenticationMode="Kerberos">  
               <localClientSettings maxClockSkew="00:07:00" />  
               <localServiceSettings maxClockSkew="00:07:00" />  
               <secureConversationBootstrap>  
                  <localClientSettings maxClockSkew="00:30:00" />  
                  <localServiceSettings maxClockSkew="00:30:00" />  
               </secureConversationBootstrap>  
            </security>  
            <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="86d23-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86d23-137">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="86d23-138">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="86d23-138">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
