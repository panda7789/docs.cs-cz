---
title: 'Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PrincipalPermissionAttribute class
- WCF, authorization
- WCF, security
ms.assetid: 5162f5c4-8781-4cc4-9425-bb7620eaeaf4
ms.openlocfilehash: 2bbdcc8e5a55f9d2cdbb80bf83443f0ad8850452
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105284"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute
Řízení přístupu k prostředkům v počítači domény Windows je úloha základní zabezpečení. Například pouze určití uživatelé by měl moct prohlížet citlivá data, jako je například mzdové informace. Toto téma vysvětluje, jak omezit přístup k metodě tak náročné, do které uživatel patří do předdefinované skupiny. Pracovní ukázku najdete v tématu [autorizace přístupu k operacím služby](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Úloha se skládá ze dvou samostatných postupů. První skupině vytvoří a naplní ho s uživateli. Druhá <xref:System.Security.Permissions.PrincipalPermissionAttribute> tak, aby určovala skupině.  
  
### <a name="to-create-a-windows-group"></a>Vytvoření skupiny Windows  
  
1.  Otevřít **Správa počítače** konzoly.  
  
2.  Na levém panelu klikněte na tlačítko **místní uživatelé a skupiny**.  
  
3.  Klikněte pravým tlačítkem na **skupiny**a klikněte na tlačítko **nová skupina**.  
  
4.  V **název skupiny** zadejte název nové skupiny.  
  
5.  V **popis** zadejte popis nové skupiny.  
  
6.  Klikněte na tlačítko **přidat** tlačítko pro přidání nových členů do skupiny.  
  
7.  Pokud sami přidali do skupiny a chcete ho testovat následující kód, musíte počítač odhlásit a znovu přihlásit, aby se součástí skupiny.  
  
### <a name="to-demand-user-membership"></a>Na vyžádání členství uživatelů  
  
1.  Otevřete soubor kódu služby Windows Communication Foundation (WCF), která obsahuje kód kontraktu služby implementované. Další informace o implementaci kontraktu a najdete v tématu [implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2.  Použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut pro každou metodu, která musí být omezeno na konkrétní skupinu. Nastavte <xref:System.Security.Permissions.SecurityAttribute.Action%2A> vlastnost <xref:System.Security.Permissions.SecurityAction.Demand> a <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> nastavte název skupiny. Příklad:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    >  Pokud použijete <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut na smlouvu <xref:System.Security.SecurityException> bude vyvolána výjimka. Lze použít pouze atribut na úrovni metody.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Použití certifikátu pro řízení přístupu k metodě  
 Můžete také použít `PrincipalPermissionAttribute` třídy pro řízení přístupu k metodu, pokud typ pověření klienta je certifikát. Chcete-li to provést, musí mít předmětu a kryptografický otisk certifikátu.  
  
 Pokud chcete prozkoumat certifikát pro jeho vlastnosti, přečtěte si téma [jak: Zobrazení certifikátů pomocí modulu Snap-in konzoly MMC](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md). Hodnoty kryptografického otisku, najdete v tématu [jak: Načtení kryptografického otisku certifikátu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Řízení přístupu k použití certifikátu  
  
1.  Použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> třídy chcete omezit přístup k metodě.  
  
2.  Nastavte akci atribut, který chcete <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3.  Nastavte `Name` nastavte na řetězec, který se skládá z názvu předmětu a kryptografický otisk certifikátu. Oddělení dvě hodnoty středník a mezeru, jak je znázorněno v následujícím příkladu:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4.  Nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> jak je znázorněno v následujícím příkladu konfigurace:  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Tuto hodnotu nastavíte na `UseAspNetRoles` znamená, že `Name` vlastnost `PrincipalPermissionAttribute` se použije k provádění porovnání řetězců. Když je certifikát použit jako pověření klienta, ve výchozím nastavení WCF zřetězí běžný název certifikátu a kryptografický otisk oddělte středníkem. Chcete-li vytvořit jedinečnou hodnotu pro klienta primární identity. S `UseAspNetRoles` nastavit jako `PrincipalPermissionMode` ve službě, tato hodnota primární identity je ve srovnání s `Name` hodnota vlastnosti k určení oprávnění uživatele.  
  
     Můžete také nastavit při vytváření služby v místním prostředí, <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastností v kódu, jak je znázorněno v následujícím kódu:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Autorizace přístupu k operacím služby](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
