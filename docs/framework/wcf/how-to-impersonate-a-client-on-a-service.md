---
title: 'Postupy: Zosobnění klienta ve službě'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, impersonation
- impersonation
- WCF, security
ms.assetid: 431db851-a75b-4009-9fe2-247243d810d3
ms.openlocfilehash: 34650a2a6cc32e16581e692b55d24d2fe02b6884
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320964"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Postupy: Zosobnění klienta ve službě
Zosobnění klienta ve službě Windows Communication Foundation (WCF) umožňuje službě provádět akce jménem klienta. U akcí, které se týkají kontrol seznamu řízení přístupu (ACL), jako je například přístup k adresářům a souborům v počítači nebo přístup k databázi SQL Server, se kontrola seznamu ACL vztahuje na uživatelský účet klienta. V tomto tématu se dozvíte o základních krocích potřebných k tomu, aby klient v doméně Windows nastavil úroveň zosobnění klienta. Pracovní příklad najdete v tématu [zosobnění klienta](./samples/impersonating-the-client.md). Další informace o zosobnění klienta najdete v tématu [delegování a zosobnění](./feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
> Když je klient a služba spuštěná ve stejném počítači a klient nástroje je spuštěný pod účtem System (tj. `Local System` nebo `Network Service`), klient se nedá zosobnit, když se naváže zabezpečená relace s tokeny kontextového kontextu zabezpečení. Modul WinForms nebo Konzolová aplikace se obvykle spouští pod aktuálně přihlášeným účtem, takže účet může být ve výchozím nastavení zosobněn. Pokud je však klient ASP.NET stránka a tato stránka je hostována ve službě IIS 6,0 nebo IIS 7,0, klient ve výchozím nastavení spustí účet `Network Service`. Všechny vazby poskytnuté systémem, které podporují zabezpečené relace, používají ve výchozím nastavení token kontextu zabezpečení bez stavů. Pokud je však klient ASP.NET stránku a jsou použity zabezpečené relace s tokeny kontextového kontextu zabezpečení, nelze klienta zosobnit. Další informace o použití tokenů kontextového kontextu zabezpečení v zabezpečené relaci naleznete v tématu [How to: Create a Security Context token pro zabezpečenou relaci](./feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Povolení zosobnění klienta od tokenu Windows uloženého v mezipaměti ve službě  
  
1. Vytvořte službu. Kurz tohoto základního postupu najdete v tématu [Začínáme kurzu](getting-started-tutorial.md).  
  
2. Použijte vazbu, která používá ověřování systému Windows, a vytvoří relaci, například <xref:System.ServiceModel.NetTcpBinding> nebo <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Při vytváření implementace rozhraní služby použijte třídu <xref:System.ServiceModel.OperationBehaviorAttribute> na metodu, která vyžaduje zosobnění klienta. Nastavte vlastnost <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> na hodnotu <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Nastavení povolené úrovně zosobnění u klienta  
  
1. Kód klienta služby vytvoříte pomocí nástroje pro tvorbu [metadat ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace najdete v tématu [přístup ke službám pomocí klienta WCF](accessing-services-using-a-wcf-client.md).  
  
2. Po vytvoření klienta služby WCF nastavte vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> třídy <xref:System.ServiceModel.Security.WindowsClientCredential> na jednu z hodnot výčtu <xref:System.Security.Principal.TokenImpersonationLevel>.  
  
    > [!NOTE]
    > Aby bylo možné použít <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>, je třeba použít vyjednané ověřování protokolem Kerberos (někdy označované jako *multi-nohy* nebo *multi-step* Kerberos). Popis toho, jak to provést, najdete v tématu [osvědčené postupy pro zabezpečení](./feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [Zosobnění klienta](./samples/impersonating-the-client.md)
- [Delegace a zosobnění](./feature-details/delegation-and-impersonation-with-wcf.md)
