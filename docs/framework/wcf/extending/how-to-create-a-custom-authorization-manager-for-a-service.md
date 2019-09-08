---
title: 'Postupy: Vytvoření vlastního správce autorizací pro službu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Communication Foundation, extending
- OperationRequirement class
ms.assetid: 6214afde-44c1-4bf5-ba07-5ad6493620ea
ms.openlocfilehash: 9c28cb81b78f80505cfcf5f7e4dfdba083bd0793
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797110"
---
# <a name="how-to-create-a-custom-authorization-manager-for-a-service"></a>Postupy: Vytvoření vlastního správce autorizací pro službu

Infrastruktura modelu identity ve službě Windows Communication Foundation (WCF) podporuje rozšiřitelný autorizační model založený na deklaracích. Deklarace identity se extrahují z tokenů a volitelně se zpracovávají pomocí vlastních zásad autorizace a <xref:System.IdentityModel.Policy.AuthorizationContext>pak se umístí do. Správce autorizací prověřuje deklarace v <xref:System.IdentityModel.Policy.AuthorizationContext> nástroji a provede rozhodnutí o autorizaci.

Ve výchozím nastavení se provádí <xref:System.ServiceModel.ServiceAuthorizationManager> rozhodnutí o autorizaci třídou. Tato rozhodnutí ale můžete přepsat vytvořením vlastního Správce autorizací. Chcete-li vytvořit vlastního Správce autorizací, vytvořte třídu, která je <xref:System.ServiceModel.ServiceAuthorizationManager> odvozena <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> z metody a implementovat metodu. Autorizační rozhodnutí se provádí v <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> metodě, která vrací `true` po udělení přístupu a `false` odepření přístupu.

Pokud autorizační rozhodnutí závisí na obsahu zprávy, použijte <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> metodu.

Z důvodu problémů s výkonem byste měli, pokud je to možné, změnit návrh aplikace tak, aby autorizační rozhodnutí nevyžadovalo přístup k textu zprávy.

Registraci vlastního Správce autorizací pro službu je možné provést v kódu nebo v konfiguraci.

### <a name="to-create-a-custom-authorization-manager"></a>Vytvoření vlastního Správce autorizací

1. Odvodit třídu od <xref:System.ServiceModel.ServiceAuthorizationManager> třídy.

    [!code-csharp[c_CustomAuthMgr#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#5)]
    [!code-vb[c_CustomAuthMgr#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#5)]

2. Přepsat <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metody.

    K provedení autorizačních rozhodnutí použijte <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%28System.ServiceModel.OperationContext%29> metodu ,kterájepředánametodě.<xref:System.ServiceModel.OperationContext>

    Následující příklad kódu používá <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%28System.String%2CSystem.String%29> metodu k vyhledání vlastní deklarace identity `http://www.contoso.com/claims/allowedoperation` k rozhodnutí o autorizaci.

    [!code-csharp[c_CustomAuthMgr#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#6)]
    [!code-vb[c_CustomAuthMgr#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#6)]

### <a name="to-register-a-custom-authorization-manager-using-code"></a>Registrace vlastního Správce autorizací pomocí kódu

1. Vytvořte instanci vlastního Správce autorizací a přiřaďte ji k <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.ServiceAuthorizationManager%2A> vlastnosti.

    K <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> poli lze použít <xref:System.ServiceModel.ServiceHostBase.Authorization%2A> vlastnost.

    Následující příklad kódu registruje `MyServiceAuthorizationManager` vlastního Správce autorizací.

    [!code-csharp[c_CustomAuthMgr#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#4)]
    [!code-vb[c_CustomAuthMgr#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#4)]

### <a name="to-register-a-custom-authorization-manager-using-configuration"></a>Registrace vlastního Správce autorizací pomocí konfigurace

1. Otevřete konfigurační soubor pro službu.

2. Přidejte [> serviceAuthorization do > chování. \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) [ \<](../../configure-apps/file-schema/wcf/behaviors.md)

    `serviceAuthorizationManagerType` [Do serviceAuthorization > přidejte atribut a nastavte jeho hodnotu na typ, který představuje vlastního Správce autorizací. \<](../../configure-apps/file-schema/wcf/serviceauthorization-element.md)

3. Přidejte vazbu, která zabezpečuje komunikaci mezi klientem a službou.

    Vazba, která je zvolena pro tuto komunikaci <xref:System.IdentityModel.Policy.AuthorizationContext>, určuje deklarace identity, které jsou přidány do, který vlastní Správce autorizací používá k rozhodování o autorizaci. Další informace o vazbách poskytovaných systémem najdete v tématu [vazby poskytované systémem](../system-provided-bindings.md).

4. Přidružte chování ke koncovému bodu služby přidáním `behaviorConfiguration` [ \<prvku > služby](../../configure-apps/file-schema/wcf/service.md) a nastavte hodnotu atributu na [ \<](../../configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) hodnotu atributu název pro > elementu behavior.

    Další informace o konfiguraci koncového bodu služby najdete v [tématu How to: V konfiguraci](../feature-details/how-to-create-a-service-endpoint-in-configuration.md)vytvořte koncový bod služby.

    Následující příklad kódu registruje vlastního správce `Samples.MyServiceAuthorizationManager`autorizací.

    ```xml
    <configuration>
      <system.serviceModel>
        <services>
          <service
              name="Microsoft.ServiceModel.Samples.CalculatorService"
              behaviorConfiguration="CalculatorServiceBehavior">
            <host>
              <baseAddresses>
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>
              </baseAddresses>
            </host>
            <endpoint address=""
                      binding="wsHttpBinding_Calculator"
                      contract="Microsoft.ServiceModel.Samples.ICalculator" />
          </service>
        </services>
        <bindings>
          <WSHttpBinding>
           <binding name = "wsHttpBinding_Calculator">
             <security mode="Message">
               <message clientCredentialType="Windows"/>
             </security>
            </binding>
          </WSHttpBinding>
        </bindings>
        <behaviors>
          <serviceBehaviors>
            <behavior name="CalculatorServiceBehavior">
              <serviceAuthorization serviceAuthorizationManagerType="Samples.MyServiceAuthorizationManager,MyAssembly" />
             </behavior>
         </serviceBehaviors>
       </behaviors>
      </system.serviceModel>
    </configuration>
    ```

    > [!WARNING]
    > Všimněte si, že když zadáte serviceAuthorizationManagerType, řetězec musí obsahovat plně kvalifikovaný název typu. čárka a název sestavení, ve kterém je definován typ. Pokud necháte název sestavení, služba WCF se pokusí načíst typ ze souboru System. ServiceModel. dll.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje základní implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídy, která obsahuje <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccessCore%2A> přepsání metody. Vzorový kód kontroluje vlastní deklaraci <xref:System.IdentityModel.Policy.AuthorizationContext> identity a vrátí `true` , když prostředek pro tuto vlastní deklaraci identity odpovídá hodnotě akce z <xref:System.ServiceModel.OperationContext>. Úplnější implementaci <xref:System.ServiceModel.ServiceAuthorizationManager> třídy najdete v tématu [zásady autorizace](../samples/authorization-policy.md).

[!code-csharp[c_CustomAuthMgr#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customauthmgr/cs/c_customauthmgr.cs#2)]
[!code-vb[c_CustomAuthMgr#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customauthmgr/vb/c_customauthmgr.vb#2)]

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceAuthorizationManager>
- [Zásady autorizace](../samples/authorization-policy.md)
