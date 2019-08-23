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
ms.openlocfilehash: 3b109e3e6817c300af1e79258d555562dcba067a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951010"
---
# <a name="how-to-restrict-access-with-the-principalpermissionattribute-class"></a>Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute
Řízení přístupu k prostředkům v počítači se systémem Windows je základní úloha zabezpečení. Například jenom někteří uživatelé by měli být schopni zobrazit citlivá data, jako jsou mzdové údaje. Toto téma vysvětluje, jak omezit přístup k metodě tím, že vyžaduje, aby uživatel patřil do předdefinované skupiny. Pracovní ukázku najdete v tématu [autorizace přístupu k operacím služby](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md).  
  
 Úkol se skládá ze dvou samostatných postupů. První vytvoří skupinu a naplní ji uživateli. Druhý použije <xref:System.Security.Permissions.PrincipalPermissionAttribute> třídu k určení skupiny.  
  
### <a name="to-create-a-windows-group"></a>Vytvoření skupiny systému Windows  
  
1. Otevřete konzolu **Správa počítače** .  
  
2. Na levém panelu klikněte na **místní uživatelé a skupiny**.  
  
3. Klikněte pravým tlačítkem na **skupiny**a pak klikněte na **Nová skupina**.  
  
4. Do pole **název skupiny** zadejte název nové skupiny.  
  
5. Do pole **Popis** zadejte popis nové skupiny.  
  
6. Kliknutím na tlačítko **Přidat** přidejte do skupiny nové členy.  
  
7. Pokud jste do skupiny přidali sami sebe a chcete otestovat následující kód, musíte se odhlásit od počítače a znovu se přihlásit, aby byl zahrnutý do skupiny.  
  
### <a name="to-demand-user-membership"></a>Pro vyžádání členství uživatele  
  
1. Otevřete soubor kódu Windows Communication Foundation (WCF), který obsahuje implementovaný kód kontraktu služby. Další informace o implementaci kontraktu najdete v tématu [implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
2. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Použijte atribut pro každou metodu, která musí být omezena na konkrétní skupinu. Nastavte vlastnost na <xref:System.Security.Permissions.SecurityAction.Demand> a<xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A> vlastnost na název skupiny. <xref:System.Security.Permissions.SecurityAttribute.Action%2A> Příklad:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#1)]
     [!code-vb[c_PrincipalPermissionAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#1)]  
  
    > [!NOTE]
    > Použijete <xref:System.Security.Permissions.PrincipalPermissionAttribute> -li atribut na kontrakt a <xref:System.Security.SecurityException> , bude vyvolána. Atribut lze použít pouze na úrovni metody.  
  
## <a name="using-a-certificate-to-control-access-to-a-method"></a>Použití certifikátu pro řízení přístupu k metodě  
 Můžete také použít `PrincipalPermissionAttribute` třídu pro řízení přístupu k metodě, pokud je typ přihlašovacích údajů klienta certifikát. K tomu je potřeba, abyste měli předmět a kryptografický otisk certifikátu.  
  
 Chcete-li si prohlédnout certifikát pro jeho vlastnosti [, přečtěte si téma How to: Zobrazení certifikátů pomocí modulu snap-in](../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)konzoly MMC. Chcete-li zjistit hodnotu kryptografického [otisku, přečtěte si téma How to: Načtení kryptografického otisku certifikátu](../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
#### <a name="to-control-access-using-a-certificate"></a>Řízení přístupu pomocí certifikátu  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute> Použijte třídu na metodu, ke které chcete omezit přístup.  
  
2. Nastavte akci atributu na <xref:System.Security.Permissions.SecurityAction.Demand?displayProperty=nameWithType>.  
  
3. `Name` Nastavte vlastnost na řetězec, který se skládá z názvu subjektu a otisku certifikátu. Tyto dvě hodnoty oddělte středníkem a mezerou, jak je znázorněno v následujícím příkladu:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#2)]
     [!code-vb[c_PrincipalPermissionAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#2)]  
  
4. Nastavte vlastnost na <xref:System.ServiceModel.Description.PrincipalPermissionMode.UseAspNetRoles> , jak je znázorněno v následujícím příkladu konfigurace: <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A>  
  
    ```xml  
    <behaviors>  
      <serviceBehaviors>  
      <behavior name="SvcBehavior1">  
      <serviceAuthorization principalPermissionMode="UseAspNetRoles" />  
      </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
     Nastavení této hodnoty na `UseAspNetRoles` označuje `Name` , že vlastnost `PrincipalPermissionAttribute` pro bude použita k porovnání řetězců. Pokud se certifikát používá jako přihlašovací údaje klienta, ve výchozím nastavení služba WCF zřetězí běžný název certifikátu a kryptografický otisk středníkem, aby vytvořil jedinečnou hodnotu pro primární identitu klienta. U `UseAspNetRoles` `Name` nastavení `PrincipalPermissionMode` ve službě je tato primární hodnota identity porovnána s hodnotou vlastnosti, aby bylo možné určit přístupová práva uživatele.  
  
     Případně při vytváření samoobslužné služby nastavte <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A> vlastnost v kódu, jak je znázorněno v následujícím kódu:  
  
     [!code-csharp[c_PrincipalPermissionAttribute#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#3)]
     [!code-vb[c_PrincipalPermissionAttribute#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- <xref:System.Security.Permissions.SecurityAction.Demand>
- <xref:System.Security.Permissions.PrincipalPermissionAttribute.Role%2A>
- [Autorizace přístupu k operacím služby](../../../docs/framework/wcf/samples/authorizing-access-to-service-operations.md)
- [Přehled zabezpečení](../../../docs/framework/wcf/feature-details/security-overview.md)
- [Implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md)
