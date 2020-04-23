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
ms.openlocfilehash: dd2a9c4485e151d4cb1c9d5ae3a95a69fcc416d4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053583"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Postupy: Určení kontextu zabezpečení pro služby
Ve výchozím nastavení se služby spouštějí v jiném kontextu zabezpečení než přihlášený uživatel. Služby jsou spuštěny v kontextu výchozího systémového účtu, který je `LocalSystem`volán s různými přístupovými oprávněními k systémovým prostředkům, než uživatel. Toto chování můžete změnit tak, aby určovalo jiný uživatelský účet, pod kterým by měla služba běžet.  
  
 Kontext zabezpečení můžete nastavit tak, že budete pracovat <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> s vlastností procesu, ve kterém je služba spuštěná. Tato vlastnost umožňuje nastavit službu na jeden ze čtyř typů účtů:  
  
- `User`, což způsobí, že systém vyzve k zadání platného uživatelského jména a hesla, když je služba nainstalovaná a běží v kontextu účtu zadaného jedním uživatelem v síti.  
  
- `LocalService`, který běží v kontextu účtu, který funguje jako Neprivilegovaný uživatel v místním počítači, a prezentuje anonymní přihlašovací údaje pro všechny vzdálené servery.  
  
- `LocalSystem`, které běží v kontextu účtu, který poskytuje rozsáhlá místní oprávnění, a prezentuje přihlašovací údaje počítače na jakémkoli vzdáleném serveru.  
  
- `NetworkService`, která běží v kontextu účtu, který funguje jako Neprivilegovaný uživatel v místním počítači, a prezentuje přihlašovací údaje počítače k jakémukoli vzdálenému serveru.  
  
 Další informace najdete v tématu <xref:System.ServiceProcess.ServiceAccount> výčet.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Určení kontextu zabezpečení pro službu  
  
1. Po vytvoření služby přidejte pro ni potřebné instalační programy. Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).  
  
2. V Návrháři přejděte ke `ProjectInstaller` třídě a klikněte na instalační program procesu služby pro službu, se kterou pracujete.  
  
    > [!NOTE]
    > Pro každou aplikaci služby je ve `ProjectInstaller` třídě k dispozici alespoň dvě součásti instalace – jeden, který nainstaluje procesy pro všechny služby v projektu, a jeden instalační program pro každou službu, kterou aplikace obsahuje. V této instanci chcete vybrat <xref:System.ServiceProcess.ServiceProcessInstaller>.  
  
3. V okně **vlastnosti** nastavte <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> na odpovídající hodnotu.  
  
## <a name="see-also"></a>Viz také

- [Úvod do aplikací služby systému Windows](introduction-to-windows-service-applications.md)
- [Postupy: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md)
- [Postupy: Vytváření služeb systému Windows](how-to-create-windows-services.md)
