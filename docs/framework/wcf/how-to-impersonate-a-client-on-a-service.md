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
ms.openlocfilehash: 918cbba30cbb997a1f029a250adbdc4ed6310299
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951049"
---
# <a name="how-to-impersonate-a-client-on-a-service"></a>Postupy: Zosobnění klienta ve službě
Zosobnění klienta ve službě Windows Communication Foundation (WCF) umožňuje službě provádět akce jménem klienta. U akcí, které se týkají kontrol seznamu řízení přístupu (ACL), jako je například přístup k adresářům a souborům v počítači nebo přístup k databázi SQL Server, se kontrola seznamu ACL vztahuje na uživatelský účet klienta. V tomto tématu se dozvíte o základních krocích potřebných k tomu, aby klient v doméně Windows nastavil úroveň zosobnění klienta. Pracovní příklad najdete v tématu [zosobnění klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md). Další informace o zosobnění klienta najdete v tématu [delegování a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
> [!NOTE]
> Když je klient a služba spuštěná ve stejném počítači a klient nástroje je spuštěný pod účtem systému (tj `Local System` . nebo `Network Service`), klient se nemůže zosobnit, když se naváže zabezpečená relace s tokeny kontextového kontextu zabezpečení. Modul WinForms nebo Konzolová aplikace se obvykle spouští pod aktuálně přihlášeným účtem, takže účet může být ve výchozím nastavení zosobněn. Pokud je však klient ASP.NET stránka a tato stránka je hostována ve službě IIS 6,0 nebo IIS 7,0, bude klient ve výchozím nastavení spuštěn pod `Network Service` účtem. Všechny vazby poskytnuté systémem, které podporují zabezpečené relace, používají ve výchozím nastavení token kontextu zabezpečení bez stavů. Pokud je však klient ASP.NET stránku a jsou použity zabezpečené relace s tokeny kontextového kontextu zabezpečení, nelze klienta zosobnit. Další informace o použití tokenů kontextového kontextu zabezpečení v zabezpečené relaci naleznete v [tématu How to: Vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
### <a name="to-enable-impersonation-of-a-client-from-a-cached-windows-token-on-a-service"></a>Povolení zosobnění klienta od tokenu Windows uloženého v mezipaměti ve službě  
  
1. Vytvořte službu. Kurz tohoto základního postupu najdete v tématu [Začínáme kurzu](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
2. Použijte vazbu, která používá ověřování systému Windows, a vytvoří relaci, například <xref:System.ServiceModel.NetTcpBinding> nebo <xref:System.ServiceModel.WSHttpBinding>.  
  
3. Při vytváření implementace rozhraní služby použijte <xref:System.ServiceModel.OperationBehaviorAttribute> třídu na metodu, která vyžaduje zosobnění klienta. Nastavte <xref:System.ServiceModel.OperationBehaviorAttribute.Impersonation%2A> vlastnost <xref:System.ServiceModel.ImpersonationOption.Required>.  
  
     [!code-csharp[c_SimpleImpersonation#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#2)]
     [!code-vb[c_SimpleImpersonation#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#2)]  
  
### <a name="to-set-the-allowed-impersonation-level-on-the-client"></a>Nastavení povolené úrovně zosobnění u klienta  
  
1. Kód klienta služby vytvoříte pomocí nástroje pro tvorbu [metadat ServiceModel (Svcutil. exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Další informace najdete v tématu [přístup ke službám pomocí klienta WCF](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).  
  
2. Po vytvoření klienta služby WCF nastavte <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> vlastnost <xref:System.ServiceModel.Security.WindowsClientCredential> <xref:System.Security.Principal.TokenImpersonationLevel> třídy na jednu z hodnot výčtu.  
  
    > [!NOTE]
    > Chcete- <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>li použít, je třeba použít dohodnuté ověřování protokolem Kerberos (někdy označované jako *multi-nohy* nebo *multi-step* Kerberos). Popis toho, jak to provést, najdete v tématu [osvědčené postupy pro zabezpečení](../../../docs/framework/wcf/feature-details/best-practices-for-security-in-wcf.md).  
  
     [!code-csharp[c_SimpleImpersonation#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_simpleimpersonation/cs/source.cs#1)]
     [!code-vb[c_SimpleImpersonation#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_simpleimpersonation/vb/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.OperationBehaviorAttribute>
- <xref:System.Security.Principal.TokenImpersonationLevel>
- [Zosobnění klienta](../../../docs/framework/wcf/samples/impersonating-the-client.md)
- [Delegace a zosobnění](../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
