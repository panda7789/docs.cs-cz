---
title: "Postupy: Určení kontextu zabezpečení pro služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Service applications, security
- security [Visual Studio], contexts
- contexts, Visual Studio security
- security [Visual Studio], service applications
- ServiceProcessInstaller class, security context
- services, security
- ServiceInstaller class, security context
ms.assetid: 02187c7b-dbf2-45f2-96c2-e11010225a22
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: douge
ms.openlocfilehash: 50a9c6ff7f02cda4475aa5390181fa5d410af161
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Úvod do aplikace služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Postupy: vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
