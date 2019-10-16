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
ms.openlocfilehash: d62011728b6b03023ef4039480cea8dfa0ec8f02
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321289"
---
# <a name="how-to-specify-the-client-credential-type"></a>Postupy: Určení typu pověření klienta
Po nastavení režimu zabezpečení (přenosu nebo zprávy) máte možnost nastavit typ přihlašovacích údajů klienta. Tato vlastnost určuje, jaký typ pověření musí klient poskytnout službě k ověřování. Další informace o nastavení režimu zabezpečení (nezbytný krok před nastavením typu pověření klienta) najdete v tématu [How to: set a Security Mode](how-to-set-the-security-mode.md).  
  
### <a name="to-set-the-client-credential-type-in-code"></a>Nastavení typu pověření klienta v kódu  
  
1. Vytvořte instanci vazby, kterou bude služba používat. V tomto příkladu se používá vazba <xref:System.ServiceModel.WSHttpBinding>.  
  
2. Nastavte vlastnost <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> na odpovídající hodnotu. V tomto příkladu se používá režim zprávy.  
  
3. Nastavte vlastnost <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> na odpovídající hodnotu. V tomto příkladu se nastaví pro použití ověřování systému Windows (<xref:System.ServiceModel.MessageCredentialType.Windows>).  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a>Nastavení typu pověření klienta v konfiguraci  
  
1. Přidejte do konfiguračního souboru prvek [\<System. serviceModel >](../configure-apps/file-schema/wcf/system-servicemodel.md) .  
  
2. Jako podřízený element přidejte [> prvek \<bindings](../configure-apps/file-schema/wcf/bindings.md) .  
  
3. Přidejte odpovídající vazbu. V tomto příkladu se používá [> prvek \<wsHttpBinding](../configure-apps/file-schema/wcf/wshttpbinding.md) .  
  
4. Přidejte prvek [> \<binding](../misc/binding.md) a nastavte atribut `name` na odpovídající hodnotu. V tomto příkladu se používá název "SecureBinding".  
  
5. Přidejte vazbu `<security>`. Nastavte atribut `mode` na odpovídající hodnotu. V tomto příkladu se nastaví na hodnotu `"Message"`.  
  
6. Přidejte buď prvek `<message>` nebo `<transport>`, jak je určeno režimem zabezpečení. Nastavte atribut `clientCredentialType` na odpovídající hodnotu. V tomto příkladu se používá `"Windows"`.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení služeb](securing-services.md)
- [Postupy: Nastavení režimu zabezpečení](how-to-set-the-security-mode.md)
