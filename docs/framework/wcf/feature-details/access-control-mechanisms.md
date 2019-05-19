---
title: Mechanismy řízení přístupu
ms.date: 03/30/2017
helpviewer_keywords:
- WCF security
- access control [WCF]
ms.assetid: 9d576122-3f55-4425-9acf-b23d0781e966
ms.openlocfilehash: 9ebd1489c35bb3b023ed73cd86fac1b6a352012b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65882175"
---
# <a name="access-control-mechanisms"></a>Mechanismy řízení přístupu
Můžete řídit přístup k několika způsobem Windows Communication Foundation (WCF). Toto téma stručně popisuje různé mechanismy a nabízí návrhy k tomu, kdy se má použít. jeho účelem je pomoct vybrat správný mechanismus. Technologie pro přístup k jsou uvedeny v pořadí podle složitosti. Nejjednodušší je <xref:System.Security.Permissions.PrincipalPermissionAttribute>; nejvíce komplex nachází modelem Identity.  
  
 Kromě těchto mechanismů zosobnění a delegování s použitím technologie WCF je podrobně [delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md).  
  
## <a name="principalpermissionattribute"></a>PrincipalPermissionAttribute  
 <xref:System.Security.Permissions.PrincipalPermissionAttribute> Slouží k omezení přístupu k metodě služby. Když je atribut použit na metodu, můžete použít požadovat konkrétní volající identity nebo členství ve skupině Windows nebo rolí technologie ASP.NET. Pokud klient je ověřený pomocí certifikátu X.509, dostane primární identitu, která se skládá z názvu předmětu a kryptografický otisk certifikátu.  
  
 Použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> pro řízení přístupu k prostředkům v počítači, který je služba spuštěna, a pokud uživatelé služby bude vždy součástí stejné domény Windows, na kterém služba běží na. Můžete snadno vytvořit skupin Windows, které jste zadali úrovně přístupu (jako jsou none, jen pro čtení, nebo čtení a zápis).  
  
 Další informace o použití atributu najdete v tématu [jak: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md). Další informace o identitě najdete v tématu [identita a ověřování služby](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
## <a name="aspnet-membership-provider"></a>Zprostředkovatel členství technologie ASP.NET  
 Funkce technologie ASP.NET je zprostředkovatel členství. I když zprostředkovatel členství není technicky mechanismus řízení přístupu, umožňuje řízení přístupu ke službě tím, že omezíte sadu možných identity, které můžete přístup ke koncovému bodu služby. Funkce členství zahrnuje databáze, která je možné naplnit kombinace uživatelské jméno/heslo, které umožňují uživatelům webu vytvářet účty s lokalitou. Přístup ke službě, která používá zprostředkovatele členství, uživatel musí přihlásit pomocí své uživatelské jméno a heslo.  
  
> [!NOTE]
>  Musíte nejprve naplnit databázi pomocí funkce technologie ASP.NET ve službě WCF mohli používat pro účely ověření.  
  
 Pokud už máte databázi členství z existujícího webu technologie ASP.NET a chcete povolit stejným uživatelům pomocí služby, oprávnění pomocí stejného uživatelského jména a hesla, můžete použít také funkci členství.  
  
 Další informace o použití funkce členství ve službě WCF najdete v tématu [jak: Používání poskytovatele členství ASP.NET](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-membership-provider.md).  
  
## <a name="aspnet-role-provider"></a>Zprostředkovatele rolí ASP.NET  
 Další funkcí technologie ASP.NET je schopnost spravovat autorizaci s použitím rolí. Poskytovatele rolí prostředí ASP.NET umožňuje vývojáři k vytvoření role pro uživatele a přiřadit každého uživatele k roli nebo role. Stejně jako u zprostředkovatele členství, role a přiřazení jsou uloženy v databázi a je možné naplnit s použitím nástroje poskytované systémem konkrétní implementaci poskytovatele rolí prostředí ASP.NET. Stejně jako u funkce členství vývojáře technologie WCF. můžete použít informace v databázi k autorizaci uživatelů služby role. Zprostředkovatel rolí můžou, například použít v kombinaci s `PrincipalPermissionAttribute` výše popsané mechanismu řízení přístupu.  
  
 Můžete také použít poskytovatele rolí prostředí ASP.NET, pokud máte existující databázi zprostředkovatele rolí ASP.NET a chcete použít stejnou sadu pravidel a přiřazení uživatele ve službě WCF.  
  
 Další informace o používání funkcí zprostředkovatele rolí, najdete v části [jak: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md).  
  
## <a name="authorization-manager"></a>Správce autorizací  
 Další funkcí kombinuje Správce autorizací (AzMan) s poskytovatele rolí prostředí ASP.NET, které zajistí autorizaci klientů. Když technologie ASP.NET je hostitelem webové služby, je možné integrovat AzMan do aplikace tak, aby autorizace ve službě se provádí prostřednictvím AzMan. Správce rolí technologie ASP.NET poskytuje rozhraní API, které vám umožní spravovat aplikačních rolí, přidávat a odebírat uživatele z role a zkontrolujte členství v roli, ale neumožňuje zadat dotaz, zda je uživatel oprávnění k provedení s názvem úkolu nebo operace. AzMan umožňuje definovat jednotlivé operace a je zkombinovat do úlohy. S AZMan kromě kontroly role můžete také zkontrolovat, jestli může uživatel provést úlohu. Přiřazení a úkol autorizaci rolí můžete nakonfigurovat mimo aplikaci nebo programově provádět v rámci aplikace. Správa AzMan modul snap-in konzoly Microsoft Management Console (MMC) umožňuje správcům ke změně úlohy, které může role provádět v době běhu a spravovat každý uživatel členství rolí.  
  
 Pokud již máte přístup do existující instalace AzMan a autorizovat uživatele služby pomocí funkce kombinace poskytovatele AzMan/role, můžete použít také AzMan a poskytovatele rolí prostředí ASP.NET.  
  
 Další informace o AzMan a poskytovatele rolí prostředí ASP.NET, naleznete v tématu [How To: Použití Správce autorizací (AzMan) s technologií ASP.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=88951). Další informace o používání AzMan a zprostředkovatel rolí pro služby WCF najdete v tématu [jak: Použití zprostředkovatele Role Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md).  
  
## <a name="identity-model"></a>Modelem identity  
 Identity Model je sada rozhraní API, která vám umožní spravovat deklarací identity a zásady k autorizaci klientů. S modelem Identity můžete prozkoumat každou deklarací identity obsažených v přihlašovacích údajích, založené na porovnání volající použít k svému ověření ke službě, porovnávání deklarací identity do sady zásad pro službu a udělit nebo odepřít přístup.  
  
 Model identit použijte, pokud potřebujete jemné ovládacího prvku a možnost nastavit konkrétní kritéria před udělením přístupu. Například při použití <xref:System.Security.Permissions.PrincipalPermissionAttribute>, že kritérium představuje jednoduše, že identita uživatele je ověřený a patří do určité role. Naproti tomu pomocí modelu identit, můžete vytvořit zásadu, která uvádí, uživatel musí být starší 18 let a má platný ovladač licence povolení k zobrazení dokumentu.  
  
 Jeden příklad, ve kterém můžete využívat výhod řízení přístupu podle deklarací Identity modelu je při použití přihlašovacích údajů federace ve scénáři vydaných tokenů. Další informace o federace a vystavené tokeny, naleznete v tématu [federace a vydané tokeny](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
 Další informace o modelem Identity najdete v tématu [správa deklarací identity a autorizace s modelem Identity](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Security.Permissions.PrincipalPermissionAttribute>
- [Postupy: Omezení přístupu pomocí třídy PrincipalPermissionAttribute](../../../../docs/framework/wcf/how-to-restrict-access-with-the-principalpermissionattribute-class.md)
- [Postupy: Použití zprostředkovatele rolí ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-role-provider-with-a-service.md)
- [Postupy: Použití zprostředkovatele Role Správce autorizací ASP.NET se službou](../../../../docs/framework/wcf/feature-details/how-to-use-the-aspnet-authorization-manager-role-provider-with-a-service.md)
- [Správa deklarací identity a autorizace pomocí modelu identit](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Delegace a zosobnění](../../../../docs/framework/wcf/feature-details/delegation-and-impersonation-with-wcf.md)
