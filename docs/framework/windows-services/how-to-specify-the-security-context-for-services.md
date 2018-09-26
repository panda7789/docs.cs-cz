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
ms.openlocfilehash: a5a437af90f29bc601215176ad5c4fec702ddbc0
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47073716"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Postupy: Určení kontextu zabezpečení pro služby
Ve výchozím nastavení služby jsou spuštěny v kontextu zabezpečení než přihlášeným uživatelem. Volá se spouštějí v kontextu systému výchozí účet služby `LocalSystem`, která jim udělí různá přístupová oprávnění k systémových prostředků, než uživatel. Toto chování k určení jiného uživatelského účtu, pod kterým se vaše služba spouštět můžete změnit.  
  
 Nastavte kontext zabezpečení manipulací <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastnost pro proces, ve kterém je služba spuštěna. Tato vlastnost umožňuje nastavit službu do jedné ze čtyř typů účtu:  
  
-   `User`, což způsobí, že systém výzvy platné uživatelské jméno a heslo, pokud služba je nainstalována a spuštěna v kontextu účet specifikovaný v síti; jedním uživatelem  
  
-   `LocalService`, která se spouští v kontextu účtu, který funguje jako neprivilegované uživatele v místním počítači a nabízí pověření anonymního a jakémukoli vzdálenému serveru;  
  
-   `LocalSystem`, která se spouští v kontextu účtu, který poskytuje rozsáhlé místní oprávnění a zobrazení přihlašovacích údajů počítače a jakémukoli vzdálenému serveru;  
  
-   `NetworkService`, která se spouští v kontextu účtu, který funguje jako neprivilegované uživatele v místním počítači a uvede přihlašovacích údajů počítače a jakémukoli vzdálenému serveru.  
  
 Další informace najdete v tématu <xref:System.ServiceProcess.ServiceAccount> výčtu.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>K určení kontextu zabezpečení pro službu  
  
1.  Po vytvoření vaší služby, přidejte nezbytné instalační programy pro něj. Další informace najdete v tématu [postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md).  
  
2.  V návrháři pro přístup `ProjectInstaller` třídy a klikněte na instalační program služby procesu pro službu pracujete.  
  
    > [!NOTE]
    >  Pro každou aplikaci služby existují alespoň dvě součásti instalace v `ProjectInstaller` třídy – ten, který nainstaluje procesy pro všechny služby v projektu a jednoho instalačního programu pro každou službu, která obsahuje aplikaci. V této instanci, kterou chcete vybrat <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3.  V **vlastnosti** okno, nastaveno <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> na odpovídající hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Úvod do aplikací služby systému Windows](../../../docs/framework/windows-services/introduction-to-windows-service-applications.md)  
 [Postupy: Přidání instalačních programů do aplikace služby](../../../docs/framework/windows-services/how-to-add-installers-to-your-service-application.md)  
 [Postupy: Vytváření služeb systému Windows](../../../docs/framework/windows-services/how-to-create-windows-services.md)
