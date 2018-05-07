---
title: 'Postupy: Zabezpečené zprávy ve spolehlivých relacích'
ms.date: 03/30/2017
ms.assetid: aee33e50-936f-4486-9ca8-c1520c19a62d
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 4c320d74f7e7966bfa35c824dbe30da768cd1447
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Postupy: Zabezpečené zprávy ve spolehlivých relacích

Toto téma popisuje kroky potřebné k povolení zabezpečení na úrovni zpráv pro zprávy vyměňují ve spolehlivých relacích pomocí jedné vazby poskytované systémem, které podporují tyto relace, ale není ve výchozím nastavení. Povolte zabezpečené a spolehlivé relace imperativní pomocí kódu nebo deklarativně v konfiguračním souboru. Tento postup používá konfigurační soubory, které klient a služba Povolit zabezpečené a spolehlivé relace.

Tento postup se skládá ze tří následujících klíčových úlohách:

1. Zadejte, zda klient a služba výměna zpráv ve spolehlivých relacích.

1. Vyžadovat zabezpečení na úrovni zpráv v rámci spolehlivé relace.

1. Zadejte typ pověření klienta, který klient musí použít k ověření u služby.

Je důležité v první úloze, které obsahují element konfigurace koncového bodu `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem (v tomto příkladu) `MessageSecurity`. [  **\<Vazby >** ](../../../../docs/framework/misc/binding.md) konfigurační prvek pak odkazuje tento název pro nastavení Povolit spolehlivé relace `enabled` atribut [  **\<reliableSession >** ](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) element `true`. Můžete vyžadovat, aby záruky doručení jsou k dispozici ve spolehlivých relacích nastavením `ordered` atribut `true`.

Zdroj kopii příklad, na kterých je založena tento postup konfigurace, najdete v článku [spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Základní položky v druhé úloze se provádí nastavením `mode` atribut  **\<zabezpečení >** obsažené v elementu  **\<vazby >** Element klienta a služby `Message`.

Základní položky třetí úlohy se provádí nastavením `clientCredentialType` atribut  **\<zpráva >** obsažené v elementu  **\<zabezpečení >** Element klienta a služby `Certificate`.

> [!NOTE]
> Při použití zabezpečení zpráv s spolehlivé relace, spolehlivé zasílání zpráv pokus o ověření neověřené klienta, dokud místo došlo k výjimce při prvním selhání dojde k vypršení časového limitu.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurovat službu s WSHttpBinding používat spolehlivé relace

Tento postup je popsaný v [postup: Exchange zprávy v rámci spolehlivé relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace klienta s WSHttpBinding používat spolehlivé relace

Tento postup je popsaný v [postup: Exchange zprávy v rámci spolehlivé relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Nastavte režim a ClientCredentialType v konfiguraci

1. Přidat element do odpovídající vazby [  **\<vazby >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) element konfiguračního souboru. Následující příklad přidá [  **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) element.

1. Přidat  **\<vazby >** elementu a sadu jeho `name` atribut na odpovídající hodnotu. Tento příklad používá název `MessageSecurity`.

1. Přidat  **\<zabezpečení >** elementu a sadu `mode` atribut `Message`.

1. V rámci  **\<zabezpečení >** elementu, přidejte  **\<zpráva >** elementu a sadu `clientCredentialType` atribut `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
