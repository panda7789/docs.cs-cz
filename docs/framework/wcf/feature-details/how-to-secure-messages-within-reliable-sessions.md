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
# <a name="how-to-secure-messages-within-reliable-sessions"></a>Postupy: Zabezpečené zprávy ve spolehlivých relacích

Toto téma popisuje kroky potřebné k povolení zabezpečení na úrovni zprávy pro zprávy vyměňované v rámci spolehlivé relace pomocí jedné z vazeb poskytovaných systémem, které podporují takovou relaci, ale nejsou ve výchozím nastavení. Povolit zabezpečenou a spolehlivou relaci buď imperativně, pomocí kódu nebo deklarativního v konfiguračním souboru. Tento postup využívá konfigurační soubory klienta a služby k zajištění zabezpečené a spolehlivé relace.

Tento postup se skládá z následujících tří klíčových úloh:

1. Určete, že zprávy klienta a služby Exchange v rámci spolehlivé relace.

1. Vyžadovat zabezpečení na úrovni zpráv v rámci spolehlivé relace.

1. Zadejte typ přihlašovacích údajů klienta, který musí klient použít pro ověření u služby.

Je důležité v prvním úkolu, který prvek konfigurace koncového bodu obsahuje atribut `bindingConfiguration`, který odkazuje na konfiguraci vazby s názvem (v tomto příkladu) `MessageSecurity`. [ **\<vazba >** ](../../configure-apps/file-schema/wcf/bindings.md) prvek konfigurace pak na tento název odkazuje, aby se povolily spolehlivé relace, nastavením atributu `enabled` prvku [ **\<reliableSession >** ](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) na `true`. Můžete požadovat, aby v rámci spolehlivé relace byly dostupné seřazené záruky doručení nastavením atributu `ordered` na hodnotu `true`.

Zdrojovou kopii příkladu, na kterém je tato procedura Konfigurace založená, najdete v tématu [Spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md).

Základní položky druhé úlohy se dosahují nastavením atributu `mode` elementu **\<zabezpečení >** obsaženého v **\<vazby >** elementu klienta a služby na `Message`.

Základní položky třetí úlohy se dosahují nastavením atributu `clientCredentialType` **\<zprávy >** elementu obsaženého v elementu **\<Security >** klienta a služby na `Certificate`.

> [!NOTE]
> Při použití zabezpečení zpráv u spolehlivých relací se spolehlivé zasílání zpráv pokusí ověřit neověřeného klienta, dokud nedojde k vypršení časového limitu namísto vyvolání výjimky při prvním selhání.

### <a name="configure-the-service-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace služby s WSHttpBinding pro použití spolehlivé relace

Tento postup je popsaný v tématu [Postupy: Výměna zpráv v rámci spolehlivé relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="configure-the-client-with-a-wshttpbinding-to-use-a-reliable-session"></a>Konfigurace klienta s WSHttpBinding pro použití spolehlivé relace

Tento postup je popsaný v tématu [Postupy: Výměna zpráv v rámci spolehlivé relace](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-within-a-reliable-session.md).

### <a name="set-the-mode-and-clientcredentialtype-in-configuration"></a>Nastavení režimu a ClientCredentialType v konfiguraci

1. Přidejte vhodný element vazby do [ **\<vazeb >** ](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elementu konfiguračního souboru. Následující příklad přidá prvek [ **\<wsHttpBinding >** ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) .

1. Přidejte **\<vazbu >** elementu a nastavte jeho atribut `name` na odpovídající hodnotu. V příkladu se používá název `MessageSecurity`.

1. Přidejte prvek **> zabezpečení\<** a nastavte atribut `mode` na `Message`.

1. V rámci prvku **\<zabezpečení >** přidejte prvek **\<zprávy >** a nastavte atribut `clientCredentialType` na `Certificate`.

```xml
<wsHttpBinding>
  <binding name="MessageSecurity">
    <security mode="Message">
      <message clientCredentialType="Certificate" />
    </security>
  </binding>
</wsHttpBinding>
```
