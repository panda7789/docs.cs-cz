---
title: 'Postupy: Zabezpečené zprávy ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: edff27fe9649387c1922c34e72ef59d615e52b90
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141667"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="95042-102">Postupy: Zabezpečené zprávy ve spolehlivých relacích</span><span class="sxs-lookup"><span data-stu-id="95042-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="95042-103">Toto téma popisuje kroky potřebné k povolení zabezpečení na úrovni zprávy pro zprávy vyměňované v rámci spolehlivé relace pomocí jedné z vazeb poskytovaných systémem, které podporují takovou relaci, ale nejsou ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="95042-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="95042-104">Povolit zabezpečenou a spolehlivou relaci buď imperativně, pomocí kódu nebo deklarativního v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="95042-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="95042-105">Tento postup využívá konfigurační soubory klienta a služby k zajištění zabezpečené a spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="95042-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="95042-106">Tento postup se skládá z následujících tří klíčových úloh:</span><span class="sxs-lookup"><span data-stu-id="95042-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="95042-107">Určete, že zprávy klienta a služby Exchange v rámci spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="95042-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="95042-108">Vyžadovat zabezpečení na úrovni zpráv v rámci spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="95042-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="95042-109">Zadejte typ přihlašovacích údajů klienta, který musí klient použít pro ověření u služby.</span><span class="sxs-lookup"><span data-stu-id="95042-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="95042-110">Je důležité v prvním úkolu, který prvek konfigurace koncového bodu obsahuje atribut `bindingConfiguration`, který odkazuje na konfiguraci vazby s názvem (v tomto příkladu) `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="95042-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="95042-111">[ **\<vazba >** ](../../configure-apps/file-schema/wcf/bindings.md) prvek konfigurace pak na tento název odkazuje, aby se povolily spolehlivé relace, nastavením atributu `enabled` prvku [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) na `true`.</span><span class="sxs-lookup"><span data-stu-id="95042-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="95042-112">Můžete požadovat, aby v rámci spolehlivé relace byly dostupné seřazené záruky doručení nastavením atributu `ordered` na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="95042-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="95042-113">Zdrojovou kopii příkladu, na kterém je tato procedura Konfigurace založená, najdete v tématu [Spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="95042-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="95042-114">Základní položky druhé úlohy se dosahují nastavením atributu `mode` elementu **\<zabezpečení >** obsaženého v **\<vazby >** elementu klienta a služby na `Message`.</span><span class="sxs-lookup"><span data-stu-id="95042-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="95042-115">Základní položky třetí úlohy se dosahují nastavením atributu `clientCredentialType` **\<zprávy >** elementu obsaženého v elementu **\<Security >** klienta a služby na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="95042-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="95042-116">Při použití zabezpečení zpráv u spolehlivých relací se spolehlivé zasílání zpráv pokusí ověřit neověřeného klienta, dokud nedojde k vypršení časového limitu namísto vyvolání výjimky při prvním selhání.</span><span class="sxs-lookup"><span data-stu-id="95042-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="95042-117">Konfigurace služby s WSHttpBinding pro použití spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="95042-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="95042-118">Tento postup je popsaný v tématu [Postupy: Výměna zpráv v rámci spolehlivé relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="95042-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="95042-119">Konfigurace klienta s WSHttpBinding pro použití spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="95042-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="95042-120">Tento postup je popsaný v tématu [Postupy: Výměna zpráv v rámci spolehlivé relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="95042-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="95042-121">Nastavení režimu a ClientCredentialType v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="95042-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="95042-122">Přidejte vhodný element vazby do [ **\<vazeb >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="95042-122">Add an appropriate binding element to the [**\<bindings>**](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="95042-123">Následující příklad přidá prvek [ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="95042-123">The following example adds a [**\<wsHttpBinding>**](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="95042-124">Přidejte **\<vazbu >** elementu a nastavte jeho atribut `name` na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="95042-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="95042-125">V příkladu se používá název `MessageSecurity`.</span><span class="sxs-lookup"><span data-stu-id="95042-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="95042-126">Přidejte prvek **> zabezpečení\<** a nastavte atribut `mode` na `Message`.</span><span class="sxs-lookup"><span data-stu-id="95042-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="95042-127">V rámci prvku **\<zabezpečení >** přidejte prvek **\<zprávy >** a nastavte atribut `clientCredentialType` na `Certificate`.</span><span class="sxs-lookup"><span data-stu-id="95042-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
