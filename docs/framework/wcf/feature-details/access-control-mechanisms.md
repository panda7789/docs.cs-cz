---
title: Mechanismy řízení přístupu
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 7dcdcff9470a7c2777f856e8c1c2143a3a92b73b
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75938187"
---
# <a name="access-control-mechanisms"></a>Mechanismy řízení přístupu
Pomocí Windows Communication Foundation (WCF) můžete řídit přístup několika způsoby. Toto téma stručně popisuje různé mechanismy a poskytuje návrhy na jejich použití. je určena k tomu, aby vám pomohla vybrat správný mechanismus, který chcete použít. Technologie přístupu jsou uvedené v pořadí podle složitosti. Nejjednodušší je <xref:System.Security.Permissions.PrincipalPermissionAttribute>; Nejsložitější je model identity.  
  
 Kromě těchto mechanismů je popsána zosobnění a delegování pomocí WCF v tématu [delegování a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> slouží k omezení přístupu k metodě služby. Pokud se atribut použije na metodu, dá se použít k vyžádání identity konkrétního volajícího nebo členství v roli skupiny systému Windows nebo role ASP.NET. Pokud je klient ověřený pomocí certifikátu X. 509, je mu přiřazena primární identita, která se skládá z názvu subjektu a kryptografického otisku certifikátu.  
  
 Pomocí <xref:System.Security.Permissions.PrincipalPermissionAttribute> můžete řídit přístup k prostředkům v počítači, na kterém je služba spuštěná, a pokud budou uživatelé služby vždycky součástí stejné domény Windows, na které je služba spuštěná. Můžete snadno vytvořit skupiny systému Windows, které mají specifikované úrovně přístupu (například None, jen pro čtení nebo číst a zapisovat).  
  
 Další informace o použití atributu naleznete v tématu [How to: restrict Access with a PrincipalPermissionAttribute Class](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Další informace o identitě najdete v tématu [Identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Poskytovatel členství ASP.NET  
 ASP.NET je funkce poskytovatele členství. I když zprostředkovatel členství není technicky mechanismem řízení přístupu, umožňuje řídit přístup ke službě tím, že omezuje sadu možných identit, které mají přístup ke koncovému bodu služby. Funkce členství zahrnuje databázi, kterou lze naplnit kombinacemi uživatelského jména a hesla, které umožňují uživatelům webu vytvářet účty s lokalitou. Pro přístup ke službě, která používá poskytovatele členství, se uživatel musí přihlásit pomocí svého uživatelského jména a hesla.  
  
> [!NOTE]
> Nejprve musíte vyplnit databázi pomocí funkce ASP.NET, aby ji služba WCF mohla použít pro účely autorizace.  
  
 Funkci členství můžete použít také v případě, že již máte databázi členství z existujícího webu ASP.NET a chcete povolit stejným uživatelům, aby používali vaši službu, a to s oprávněním stejné uživatelské jméno a heslo.  
  
 Další informace o použití funkce členství ve službě WCF naleznete v tématu [How to: use the ASP.NET Membership Provider](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Poskytovatel rolí ASP.NET  
 Další funkcí ASP.NET je schopnost spravovat autorizaci pomocí rolí. Zprostředkovatel rolí ASP.NET umožňuje vývojářům vytvářet role pro uživatele a přiřazovat jednotlivé uživatele k rolím nebo rolím. Stejně jako u poskytovatele členství jsou role a přiřazení uloženy v databázi a lze je naplnit pomocí nástrojů poskytovaných konkrétní implementací zprostředkovatele rolí ASP.NET. Stejně jako u funkce členství mohou vývojáři WCF použít informace v databázi k autorizaci uživatelů služby podle rolí. Můžou například použít poskytovatele rolí v kombinaci s mechanismem řízení přístupu `PrincipalPermissionAttribute` popsaném výše.  
  
 Zprostředkovatele rolí ASP.NET můžete použít také v případě, že máte existující databázi zprostředkovatele role ASP.NET a chcete ve službě WCF použít stejnou sadu pravidel a přiřazení uživatelů.  
  
 Další informace o použití funkce poskytovatele rolí najdete v tématu [How to: use the ASP.NET role Provider to a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Správce autorizací  
 Další funkcí kombinuje Správce autorizací (AzMan) se zprostředkovatelem rolí ASP.NET pro autorizaci klientů. Když ASP.NET hostuje webovou službu, AzMan může být integrovaná do aplikace, aby bylo možné provést autorizaci služby prostřednictvím AzMan. Správce rolí ASP.NET poskytuje rozhraní API, které umožňuje spravovat aplikační role, přidávat a odebírat uživatele z rolí a kontrolovat členství v rolích, ale neumožňuje dotazovat se na to, jestli je uživatel autorizovaný k provedení pojmenované úlohy nebo operace. AzMan umožňuje definovat jednotlivé operace a kombinovat je do úloh. S AZMan můžete kromě kontrol rolí také zkontrolovat, jestli uživatel může provádět úlohu. Přiřazení rolí a autorizaci úloh lze nakonfigurovat mimo aplikaci nebo programově provést v rámci aplikace. Modul snap-in Správa AzMan konzoly Microsoft Management Console (MMC) umožňuje správcům měnit úkoly, které role může provádět za běhu, a spravovat členství rolí jednotlivých uživatelů.  
  
 AzMan a poskytovatele role ASP.NET můžete použít také v případě, že už máte přístup k existující instalaci AzMan a chcete autorizovat uživatele služby pomocí funkcí kombinace AzMan/role Provider.  
  
 Další informace o AzMan a zprostředkovateli rolí ASP.NET najdete v tématu [How to: use Authorization Manager (AzMan) with ASP.NET 2,0](https://docs.microsoft.com/previous-versions/msp-n-p/ff649313(v=pandp.10)). Další informace o používání AzMan a poskytovatele rolí pro služby WCF najdete v tématu [How to: use the ASP.NET Authorization Manager role Provider with a Service](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Model identity  
 Model identity je sada rozhraní API, která umožňují spravovat deklarace identity a zásady pro autorizaci klientů. Pomocí modelu identity můžete kontrolovat každou deklaraci identity obsaženou v přihlašovacích údajích, které volající použil k ověření ve službě, porovnávat deklarace identity se sadou zásad pro službu a udělovat nebo zamítnout přístup na základě porovnání.  
  
 Použijte model identity, pokud potřebujete přesné řízení a možnost nastavit konkrétní kritéria před udělením přístupu. Například při použití <xref:System.Security.Permissions.PrincipalPermissionAttribute>je kritérium jednoduše tím, že identita uživatele je ověřena a patří do konkrétní role. Na rozdíl od modelu identity můžete vytvořit zásadu, která uvádí, že uživatel musí mít více než 18 let věku a musí mít platnou licenci na ovladač, aby bylo možné dokument zobrazit.  
  
 Jedním z příkladů, kde můžete využít řízení přístupu na základě deklarace identity modelu identity, je použití federačních přihlašovacích údajů ve scénáři vydaného tokenu. Další informace o federačních a vydaných tokenech najdete v tématu [federace a vystavené tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Další informace o modelu identity najdete v tématu [Správa deklarací identity a autorizace pomocí modelu identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Postupy: Použití zprostředkovatele role Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
