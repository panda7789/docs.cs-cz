---
title: 'Postupy: Zabezpečené zprávy ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
ms.openlocfilehash: 306d0f96b5163fe5c24d270b4b9a7c1d3f499e7e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596952"
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a><span data-ttu-id="71fa7-102">Postupy: Zabezpečené zprávy ve spolehlivých relacích</span><span class="sxs-lookup"><span data-stu-id="71fa7-102">How to: Secure Messages within Reliable Sessions</span></span>

<span data-ttu-id="71fa7-103">Toto téma popisuje kroky potřebné k povolení zabezpečení na úrovni zprávy pro zprávy vyměňované v rámci spolehlivé relace pomocí jedné z vazeb poskytovaných systémem, které podporují takovou relaci, ale nejsou ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="71fa7-103">This topic outlines the steps required to enable message-level security for messages exchanged within a reliable session using one of the system-provided bindings that support such a session, but not by default.</span></span> <span data-ttu-id="71fa7-104">Povolit zabezpečenou a spolehlivou relaci buď imperativně, pomocí kódu nebo deklarativního v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="71fa7-104">Enable a secure, reliable session either imperatively by using code or declaratively in the configuration file.</span></span> <span data-ttu-id="71fa7-105">Tento postup využívá konfigurační soubory klienta a služby k zajištění zabezpečené a spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="71fa7-105">This procedure uses the client and service configuration files to enable the secure, reliable session.</span></span>

<span data-ttu-id="71fa7-106">Tento postup se skládá z následujících tří klíčových úloh:</span><span class="sxs-lookup"><span data-stu-id="71fa7-106">This procedure consists of the following three key tasks:</span></span>

1. <span data-ttu-id="71fa7-107">Určete, že zprávy klienta a služby Exchange v rámci spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="71fa7-107">Specify that the client and service exchange messages within a reliable session.</span></span>

1. <span data-ttu-id="71fa7-108">Vyžadovat zabezpečení na úrovni zpráv v rámci spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="71fa7-108">Require message-level security within the reliable session.</span></span>

1. <span data-ttu-id="71fa7-109">Zadejte typ přihlašovacích údajů klienta, který musí klient použít pro ověření u služby.</span><span class="sxs-lookup"><span data-stu-id="71fa7-109">Specify the client credential type that the client must use to be authenticated with the service.</span></span>

<span data-ttu-id="71fa7-110">Je důležité v prvním úkolu, který prvek konfigurace koncového bodu obsahuje `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem (v tomto příkladu) `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="71fa7-110">It's important in the first task that the endpoint configuration element contain a `bindingConfiguration` attribute that references a binding configuration named (in this example) `MessageSecurity`.</span></span> <span data-ttu-id="71fa7-111">[**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md)Prvek konfigurace pak na tento název odkazuje, aby povoloval spolehlivé relace nastavením `enabled` atributu [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) elementu na `true` .</span><span class="sxs-lookup"><span data-stu-id="71fa7-111">The [**\<binding>**](../../configure-apps/file-schema/wcf/bindings.md) configuration element then references this name to enable reliable sessions by setting the `enabled` attribute of the [**\<reliableSession>**](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) element to `true`.</span></span> <span data-ttu-id="71fa7-112">Můžete požadovat, aby seřazené záruky doručení byly dostupné v rámci spolehlivé relace nastavením `ordered` atributu na `true` .</span><span class="sxs-lookup"><span data-stu-id="71fa7-112">You can require that the ordered delivery assurances are available within a reliable session by setting the `ordered` attribute to `true`.</span></span>

<span data-ttu-id="71fa7-113">Zdrojovou kopii příkladu, na kterém je tato procedura Konfigurace založená, najdete v tématu [Spolehlivá relace WS](../samples/ws-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="71fa7-113">For the source copy of the example on which this configuration procedure is based, see the [WS Reliable Session](../samples/ws-reliable-session.md).</span></span>

<span data-ttu-id="71fa7-114">Základní položky druhé úlohy jsou provedeny nastavením `mode` atributu **\<security>** elementu obsaženého v **\<binding>** prvku klienta a služby na `Message` .</span><span class="sxs-lookup"><span data-stu-id="71fa7-114">The essential items of the second task are accomplished by setting the `mode` attribute of the **\<security>** element contained in the **\<binding>** element of the client and service to `Message`.</span></span>

<span data-ttu-id="71fa7-115">Podstatné položky třetí úlohy jsou provedeny nastavením `clientCredentialType` atributu **\<message>** elementu obsaženého v **\<security>** prvku klienta a služby na `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="71fa7-115">The essential items of the third task are accomplished by setting the `clientCredentialType` attribute of the **\<message>** element contained in the **\<security>** element of the client and service to `Certificate`.</span></span>

> [!NOTE]
> <span data-ttu-id="71fa7-116">Při použití zabezpečení zpráv u spolehlivých relací se spolehlivé zasílání zpráv pokusí ověřit neověřeného klienta, dokud nedojde k vypršení časového limitu namísto vyvolání výjimky při prvním selhání.</span><span class="sxs-lookup"><span data-stu-id="71fa7-116">When using message security with reliable sessions, Reliable Messaging attempts to authenticate an unauthenticated client until a timeout occurs instead of throwing an exception upon first failure.</span></span>

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="71fa7-117">Konfigurace služby s WSHttpBinding pro použití spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="71fa7-117">Configure the service with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="71fa7-118">Tento postup je popsaný v tématu [Postupy: Výměna zpráv v rámci spolehlivé relace](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="71fa7-118">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a><span data-ttu-id="71fa7-119">Konfigurace klienta s WSHttpBinding pro použití spolehlivé relace</span><span class="sxs-lookup"><span data-stu-id="71fa7-119">Configure the client with a WSHttpBinding to use a reliable session</span></span>

<span data-ttu-id="71fa7-120">Tento postup je popsaný v tématu [Postupy: Výměna zpráv v rámci spolehlivé relace](how-to-exchange-messages-within-a-reliable-session.md).</span><span class="sxs-lookup"><span data-stu-id="71fa7-120">This procedure is described in [How to: Exchange Messages Within a Reliable Session](how-to-exchange-messages-within-a-reliable-session.md).</span></span>

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a><span data-ttu-id="71fa7-121">Nastavení režimu a ClientCredentialType v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="71fa7-121">Set the mode and ClientCredentialType in configuration</span></span>

1. <span data-ttu-id="71fa7-122">Přidejte vhodný element vazby do [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="71fa7-122">Add an appropriate binding element to the [**\<bindings>**](../../configure-apps/file-schema/wcf/bindings.md) element of the configuration file.</span></span> <span data-ttu-id="71fa7-123">Následující příklad přidá [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) prvek.</span><span class="sxs-lookup"><span data-stu-id="71fa7-123">The following example adds a [**\<wsHttpBinding>**](../../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>

1. <span data-ttu-id="71fa7-124">Přidejte **\<binding>** element a nastavte jeho `name` atribut na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71fa7-124">Add a **\<binding>** element and set its `name` attribute to an appropriate value.</span></span> <span data-ttu-id="71fa7-125">V příkladu se používá název `MessageSecurity` .</span><span class="sxs-lookup"><span data-stu-id="71fa7-125">The example uses the name `MessageSecurity`.</span></span>

1. <span data-ttu-id="71fa7-126">Přidejte **\<security>** element a nastavte `mode` atribut na `Message` .</span><span class="sxs-lookup"><span data-stu-id="71fa7-126">Add a **\<security>** element and set the `mode` attribute to `Message`.</span></span>

1. <span data-ttu-id="71fa7-127">V rámci **\<security>** elementu přidejte **\<message>** element a nastavte `clientCredentialType` atribut na `Certificate` .</span><span class="sxs-lookup"><span data-stu-id="71fa7-127">Within the **\<security>** element, add a **\<message>** element and set the `clientCredentialType` attribute to `Certificate`.</span></span>

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
