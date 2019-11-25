---
title: 'Postupy: Určení typu pověření klienta'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: df18f89ee18bfa33ecc0aced617d168c805e3515
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74138575"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="dcf62-102">Postupy: Určení typu pověření klienta</span><span class="sxs-lookup"><span data-stu-id="dcf62-102">How to: Specify the Client Credential Type</span></span>
<span data-ttu-id="dcf62-103">Po nastavení režimu zabezpečení (přenosu nebo zprávy) máte možnost nastavit typ přihlašovacích údajů klienta.</span><span class="sxs-lookup"><span data-stu-id="dcf62-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="dcf62-104">Tato vlastnost určuje, jaký typ pověření musí klient poskytnout službě k ověřování.</span><span class="sxs-lookup"><span data-stu-id="dcf62-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="dcf62-105">Další informace o nastavení režimu zabezpečení (nezbytný krok před nastavením typu pověření klienta) najdete v tématu [How to: set a Security Mode](how-to-set-the-security-mode.md).</span><span class="sxs-lookup"><span data-stu-id="dcf62-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="dcf62-106">Nastavení typu pověření klienta v kódu</span><span class="sxs-lookup"><span data-stu-id="dcf62-106">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="dcf62-107">Vytvořte instanci vazby, kterou bude služba používat.</span><span class="sxs-lookup"><span data-stu-id="dcf62-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="dcf62-108">V tomto příkladu se používá vazba <xref:System.ServiceModel.WSHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="dcf62-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="dcf62-109">Vlastnost <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> nastavte na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dcf62-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="dcf62-110">V tomto příkladu se používá režim zprávy.</span><span class="sxs-lookup"><span data-stu-id="dcf62-110">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="dcf62-111">Vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> nastavte na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dcf62-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="dcf62-112">V tomto příkladu se nastaví pro použití ověřování systému Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span><span class="sxs-lookup"><span data-stu-id="dcf62-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="dcf62-113">Nastavení typu pověření klienta v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="dcf62-113">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="dcf62-114">Přidejte do konfiguračního souboru prvek [\<System. serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) .</span><span class="sxs-lookup"><span data-stu-id="dcf62-114">Add a [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="dcf62-115">Jako podřízený element přidejte [\<vazby >](../configure-apps/file-schema/wcf/bindings.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="dcf62-115">As a child element, add a [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="dcf62-116">Přidejte odpovídající vazbu.</span><span class="sxs-lookup"><span data-stu-id="dcf62-116">Add an appropriate binding.</span></span> <span data-ttu-id="dcf62-117">V tomto příkladu se používá prvek [\<wsHttpBinding >](../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="dcf62-117">This example uses the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="dcf62-118">Přidejte [\<vazbu >](../configure-apps/file-schema/wcf/bindings.md) elementu a nastavte atribut `name` na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dcf62-118">Add a [\<binding>](../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="dcf62-119">V tomto příkladu se používá název "SecureBinding".</span><span class="sxs-lookup"><span data-stu-id="dcf62-119">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="dcf62-120">Přidejte `<security>` vazby.</span><span class="sxs-lookup"><span data-stu-id="dcf62-120">Add a `<security>` binding.</span></span> <span data-ttu-id="dcf62-121">Nastavte atribut `mode` na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dcf62-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="dcf62-122">V tomto příkladu se nastaví na `"Message"`.</span><span class="sxs-lookup"><span data-stu-id="dcf62-122">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="dcf62-123">Přidejte `<message>` nebo `<transport>` element, jak určuje režim zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="dcf62-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="dcf62-124">Nastavte atribut `clientCredentialType` na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dcf62-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="dcf62-125">Tento příklad používá `"Windows"`.</span><span class="sxs-lookup"><span data-stu-id="dcf62-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dcf62-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcf62-126">See also</span></span>

- [<span data-ttu-id="dcf62-127">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="dcf62-127">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="dcf62-128">Postupy: Nastavení režimu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="dcf62-128">How to: Set the Security Mode</span></span>](how-to-set-the-security-mode.md)
