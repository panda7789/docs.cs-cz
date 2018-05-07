---
title: 'Postupy: Určení kontextu zabezpečení pro služby'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
author: ghogen
manager: douge
ms.openlocfilehash: e3e5ad7dd44dcaf1593ac80bbe6d0a367964e4e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-security-context-for-services"></a>Postupy: Určení kontextu zabezpečení pro služby
Ve výchozím nastavení služby spuštěny v odlišném kontextu zabezpečení než přihlášeného uživatele. Volá se spouštějí v kontextu systému do výchozího účtu služby `LocalSystem`, která jim udělí různých přístupová oprávnění k systémovým prostředkům než uživatele. Toto chování zadat jiný uživatelský účet, pod kterým měly být spuštěny služby, můžete změnit.  
  
 Nastavit kontext zabezpečení manipulací <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost pro proces, ve kterém je služba spuštěna. Tato vlastnost umožňuje nastavit na jedno ze čtyř typů účet služby:  
  
-   `User`, což způsobí, že systém výzvy platné uživatelské jméno a heslo, pokud služba je nainstalován a spuštěn v kontextu účtu určeného jenom jednoho konkrétního uživatele v síti;  
  
-   `LocalService`, který běží v kontextu účtu, který funguje jako uživatel bez oprávnění místního počítače a uvede anonymní přihlašovací údaje k žádnému vzdáleného serveru;  
  
-   `LocalSystem`, který běží v kontextu účtu, který poskytuje rozsáhlé místní oprávnění a zobrazení počítače přihlašovací údaje k žádnému vzdáleného serveru;  
  
-   `NetworkService`, který běží v kontextu účtu, který funguje jako uživatel bez oprávnění v místním počítači a uvede počítače přihlašovací údaje k žádnému vzdáleného serveru.  
  
 Další informace najdete v tématu <xref:System.ServiceProcess.ServiceAccount> výčtu.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Chcete-li určit kontext zabezpečení pro službu  
  
1.  Po vytvoření služby, přidejte potřebné instalační programy pro ni. Další informace najdete v tématu [postupy: Přidání instalačních programů pro vaše aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  V návrháři přístup `ProjectInstaller` třídu a klikněte na instalační program služby procesu pro službu pracujete.  
  
    > [!NOTE]
    >  Pro každou aplikaci služby existují alespoň dvě součásti instalace v `ProjectInstaller` třída – jeden, který nainstaluje procesy pro všechny služby v projektu a jeden instalační program pro každou službu, která obsahuje aplikaci. V této instanci, kterou chcete vybrat <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3.  V **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> na odpovídající hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
