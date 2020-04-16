---
title: Programování zabezpečení WCF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message security [WCF], programming overview
ms.assetid: 739ec222-4eda-4cc9-a470-67e64a7a3f10
ms.openlocfilehash: 1e82fbb266d3789a8d34109c66d9ee1d8a93c70c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463821"
---
# <a name="programming-wcf-security"></a>Programování zabezpečení WCF
Toto téma popisuje základní programovací úlohy používané k vytvoření zabezpečené aplikace WCF (Windows Communication Foundation). Toto téma se týká pouze ověřování, důvěrnosti a integrity, souhrnně označované jako *zabezpečení přenosu*. Toto téma se nevztahuje na autorizaci (řízení přístupu k prostředkům nebo službám); informace o autorizaci naleznete v tématu [Autorizace](../../../../docs/framework/wcf/feature-details/authorization-in-wcf.md).  
  
> [!NOTE]
> Pro cenný úvod do koncepty zabezpečení, zejména s ohledem na WCF, naleznete v sadě vzorů a postupů kurzy na MSDN na [scénáře, vzory a prováděcí pokyny pro vylepšení webových služeb (WSE) 3.0](https://docs.microsoft.com/previous-versions/msp-n-p/ff648183(v=pandp.10)).  
  
 Programování wcf zabezpečení je založena na třech krocích nastavení následující: režim zabezpečení, typ pověření klienta a hodnoty pověření. Tyto kroky můžete provést buď prostřednictvím kódu nebo konfigurace.  
  
## <a name="setting-the-security-mode"></a>Nastavení režimu zabezpečení  
 Následující vysvětluje obecné kroky pro programování s režimem zabezpečení v WCF:  
  
1. Vyberte jednu z předdefinovaných vazeb odpovídajících požadavkům aplikace. Seznam možností vazby naleznete v tématu [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md). Ve výchozím nastavení má téměř každá vazba povolené zabezpečení. Jedinou výjimkou <xref:System.ServiceModel.BasicHttpBinding> je třída (pomocí konfigurace, [ \<základníhttpbinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)).  
  
     Vazba, kterou vyberete určuje přenos. Například <xref:System.ServiceModel.WSHttpBinding> používá HTTP jako přenos; <xref:System.ServiceModel.NetTcpBinding> používá protokol TCP.  
  
2. Vyberte jeden z režimů zabezpečení pro vazbu. Všimněte si, že vazba, kterou vyberete, určuje dostupné volby režimu. Například <xref:System.ServiceModel.WSDualHttpBinding> neumožňuje zabezpečení přenosu (není možnost). Podobně ani <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> ani <xref:System.ServiceModel.NetNamedPipeBinding> umožňuje zabezpečení zpráv.  
  
     Máte tři možnosti:  
  
    1. `Transport`  
  
         Zabezpečení přenosu závisí na mechanismu, který používá vazba, kterou jste vybrali. Například pokud používáte `WSHttpBinding` pak mechanismus zabezpečení je Secure Sockets Layer (SSL) (také mechanismus pro protokol HTTPS). Obecně řečeno, hlavní výhodou zabezpečení přenosu je, že poskytuje dobrou propustnost bez ohledu na to, jaký přenos používáte. Má však dvě omezení: První je, že mechanismus přenosu určuje typ pověření použitý k ověření uživatele. To to je nevýhoda pouze v případě, že služba potřebuje spolupracovat s jinými službami, které vyžadují různé typy pověření. Druhým důvodem je, že vzhledem k tomu, že zabezpečení není použito na úrovni zprávy, zabezpečení je implementováno způsobem směrování a směrování spíše než end-to-end. Toto posledně uvedené omezení je problém pouze v případě, že cesta zprávy mezi klientem a službou zahrnuje zprostředkovatele. Další informace o tom, který přenos použít, naleznete v [tématu Výběr přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Další informace o použití zabezpečení přenosu naleznete v tématu [Přehled zabezpečení přenosu](../../../../docs/framework/wcf/feature-details/transport-security-overview.md).  
  
    2. `Message`  
  
         Zabezpečení zpráv znamená, že každá zpráva obsahuje potřebná záhlaví a data, aby byla zpráva zabezpečena. Vzhledem k tomu, že složení záhlaví se liší, můžete zahrnout libovolný počet pověření. To se stává faktorem, pokud spolupracujete s jinými službami, které vyžadují určitý typ pověření, který mechanismus přenosu nemůže poskytnout, nebo pokud zpráva musí být použita s více než jednou službou, kde každá služba vyžaduje jiný typ pověření.  
  
         Další informace naleznete v tématu [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).  
  
    3. `TransportWithMessageCredential`  
  
         Tato volba používá transportní vrstvu k zabezpečení přenosu zpráv, zatímco každá zpráva obsahuje bohaté přihlašovací údaje, které potřebují jiné služby. To kombinuje výhodu výkonu zabezpečení přenosu s výhodami bohaté pověření zabezpečení zpráv. Tato možnost je k dispozici <xref:System.ServiceModel.BasicHttpBinding> <xref:System.ServiceModel.WSFederationHttpBinding>s <xref:System.ServiceModel.NetPeerTcpBinding>následujícími vazbami: , , , a <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Pokud se rozhodnete použít zabezpečení přenosu pro protokol HTTP (jinými slovy HTTPS), musíte také nakonfigurovat hostitele pomocí certifikátu SSL a povolit protokol SSL na portu. Další informace naleznete v tématu [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
4. Pokud používáte <xref:System.ServiceModel.WSHttpBinding> a nepotřebujete vytvořit zabezpečenou relaci, nastavte <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost na `false`.  
  
     K zabezpečené relaci dojde, když klient a služba vytvoří kanál pomocí symetrického klíče (klient i server používají stejný klíč po dobu konverzace, dokud není dialogové okno uzavřeno).  
  
## <a name="setting-the-client-credential-type"></a>Nastavení typu pověření klienta  
 Podle potřeby vyberte typ pověření klienta. Další informace naleznete [v tématu Výběr typu pověření](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md). K dispozici jsou následující typy pověření klienta:  
  
- `Windows`  
  
- `Certificate`  
  
- `Digest`  
  
- `Basic`  
  
- `UserName`  
  
- `NTLM`  
  
- `IssuedToken`  
  
 V závislosti na nastavení režimu je nutné nastavit typ pověření. Pokud jste například vybrali `wsHttpBinding`možnost , a nastavili jste režim na `clientCredentialType` "Zpráva", můžete také nastavit atribut `None` `Windows`prvku `UserName` `Certificate`Message `IssuedToken`na jednu z následujících hodnot: , , , a , jak je znázorněno v následujícím příkladu konfigurace.  
  
```xml  
<system.serviceModel>  
<bindings>  
  <wsHttpBinding>  
    <binding name="myBinding">  
      <security mode="Message"/>  
      <message clientCredentialType="Windows"/>  
    </binding>
  </wsHttpBinding>
</bindings>  
</system.serviceModel>  
```  
  
 Nebo v kódu:  
  
 [!code-csharp[c_WsHttpService#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_wshttpservice/cs/source.cs#1)]
 [!code-vb[c_WsHttpService#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_wshttpservice/vb/source.vb#1)]  
  
## <a name="setting-service-credential-values"></a>Nastavení hodnot pověření služby  
 Jakmile vyberete typ pověření klienta, musíte nastavit skutečná pověření pro službu a klienta, které chcete použít. Ve službě jsou pověření nastavena <xref:System.ServiceModel.Description.ServiceCredentials> pomocí třídy <xref:System.ServiceModel.ServiceHostBase.Credentials%2A> a <xref:System.ServiceModel.ServiceHostBase> vrácena vlastností třídy. Použitá vazba zahrnuje typ pověření služby, zvolený režim zabezpečení a typ pověření klienta. Následující kód nastaví certifikát pro pověření služby.  
  
 [!code-csharp[c_tcpService#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#3)]
 [!code-vb[c_tcpService#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#3)]  
  
## <a name="setting-client-credential-values"></a>Nastavení hodnot pověření klienta  
 Na straně klienta nastavte hodnoty <xref:System.ServiceModel.Description.ClientCredentials> pověření klienta <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> pomocí <xref:System.ServiceModel.ClientBase%601> třídy a vrácené vlastností třídy. Následující kód nastaví certifikát jako pověření na klienta pomocí protokolu TCP.  
  
 [!code-csharp[c_TcpClient#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpclient/cs/source.cs#1)]
 [!code-vb[c_TcpClient#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpclient/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)
