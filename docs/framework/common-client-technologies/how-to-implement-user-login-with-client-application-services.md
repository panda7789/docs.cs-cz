---
title: 'Postupy: Implementace přihlášení uživatele u klientských aplikačních služeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- validating users [client application services]
- validation [.NET Framework], client application services
- client application services, authenticate users
ms.assetid: 5431a671-eb02-4e18-a651-24764fccec9a
ms.openlocfilehash: a878b12620faf9a6e9fecbd2e76644aea3d80611
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43504793"
---
# <a name="how-to-implement-user-login-with-client-application-services"></a>Postupy: Implementace přihlášení uživatele u klientských aplikačních služeb
Klientské aplikační služby můžete použít k ověření uživatelů prostřednictvím existující [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] služba profilu. Informace o tom, jak nastavit [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] Profilovat službu, najdete v článku [použití ověřování pomocí formulářů s Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e).  
  
 Následující postupy popisují, jak ověřit uživatele ve službě ověřování, pokud vaše aplikace je nakonfigurovaná pomocí jednoho z poskytovatelů služeb ověřování klienta. Další informace najdete v tématu [postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md).  
  
 Budete obvykle provádět všechny ověřovací prostřednictvím `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metody. Tato metoda spravuje interakci se službou ověřování prostřednictvím poskytovatele nakonfigurované ověřování. Další informace najdete v tématu [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md).  
  
 Postupy ověřování formulářů vyžadují přístup ke spuštěnému [!INCLUDE[ajax_current_short](../../../includes/ajax-current-short-md.md)] ověřovací službu. Doprovodné materiály k začátku do konce testování klientské aplikace služeb funkcí najdete v tématu [návod: použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
### <a name="to-authenticate-a-user-with-forms-authentication-using-a-membership-credentials-provider"></a>K ověření uživatele pomocí ověřování pomocí formulářů pomocí přihlašovacích údajů zprostředkovatele členství  
  
1.  Implementace <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider> rozhraní. Následující příklad kódu ukazuje <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A?displayProperty=nameWithType> implementace třídy dialogového okna přihlašovací jméno odvozené z <xref:System.Windows.Forms.Form?displayProperty=nameWithType>. Dialogové okno obsahuje textová pole pro uživatelské jméno a heslo a zaškrtávací políčko "pamatovat si mě". Když volá zprostředkovatele ověřování klienta <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metoda, formulář se zobrazí. Když uživatel vyplní informace v dialogovém okně přihlašovací jméno a klikne na tlačítko OK, zadané hodnoty jsou vráceny v novém <xref:System.Web.ClientServices.Providers.ClientFormsAuthenticationCredentials> objektu.  
  
     [!code-csharp[ClientApplicationServices#210](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Login.cs#210)]
     [!code-vb[ClientApplicationServices#210](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Login.vb#210)]  
  
2.  Volání `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda a předejte jí prázdné řetězce jako hodnoty parametrů. Když zadáte prázdné řetězce, interně volá tuto metodu <xref:System.Web.ClientServices.Providers.IClientFormsAuthenticationCredentialsProvider.GetCredentials%2A> metodu pro zprostředkovatele přihlašovací údaje nakonfigurované pro vaši aplikaci. Následující příklad kódu volá tuto metodu za účelem omezení přístupu k celé aplikace Windows Forms. Tento kód můžete přidat <xref:System.Windows.Forms.Form.Load?displayProperty=nameWithType> obslužné rutiny.  
  
     [!code-csharp[ClientApplicationServices#317](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#317)]
     [!code-vb[ClientApplicationServices#317](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#317)]  
  
### <a name="to-authenticate-a-user-with-forms-authentication-without-using-a-membership-credentials-provider"></a>K ověření uživatele pomocí ověřování pomocí formulářů bez použití poskytovatele pověření členství  
  
-   Volání `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metoda a předejte jí uživatelské jméno a heslo hodnoty načíst od uživatele.  
  
     [!code-csharp[ClientApplicationServices#318](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#318)]
     [!code-vb[ClientApplicationServices#318](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#318)]  
  
### <a name="to-authenticate-a-user-with-windows-authentication"></a>K ověření uživatele s ověřováním Windows  
  
-   Volání `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> a předáte prázdné řetězce pro parametry. Volání této metody vždy vrátí `true` a přidá do souboru cookie do mezipaměti souborů cookie uživatele, který obsahuje Windows identity.  
  
     [!code-csharp[ClientApplicationServices#319](../../../samples/snippets/csharp/VS_Snippets_Winforms/ClientApplicationServices/CS/Class1.cs#319)]
     [!code-vb[ClientApplicationServices#319](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ClientApplicationServices/VB/Class1.vb#319)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Příklad kódu v tomto tématu ukazuje nejjednodušší použití ověřování v klientské aplikaci Windows. Při volání `static` <xref:System.Web.Security.Membership.ValidateUser%2A?displayProperty=nameWithType> metodu se klientská aplikace služby a ověřování pomocí formulářů, ale může vyvolat kódu <xref:System.Net.WebException>. To znamená, že ověřovací služby není k dispozici. Příklad toho, jak zpracovat tuto výjimku, naleznete v tématu [návod: použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Klientské aplikační služby](../../../docs/framework/common-client-technologies/client-application-services.md)  
 [Přehled klientských aplikačních služeb](../../../docs/framework/common-client-technologies/client-application-services-overview.md)  
 [Postupy: Konfigurace klientských aplikačních služeb](../../../docs/framework/common-client-technologies/how-to-configure-client-application-services.md)  
 [Návod: Použití klientských aplikačních služeb](../../../docs/framework/common-client-technologies/walkthrough-using-client-application-services.md)  
 [Ověřování pomocí formulářů s technologií Microsoft Ajax](https://msdn.microsoft.com/library/c50f7dc5-323c-4c63-b4f3-96edfc1e815e)
