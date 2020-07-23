---
title: 'Postupy: Určení kontextu zabezpečení pro služby'
description: Určete kontext zabezpečení pro služby. Služby spuštěné ve výchozím kontextu systémového účtu mají jiná přístupová práva k systémovému prostředku než přihlášený uživatel.
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
ms.openlocfilehash: 4ed531cb520a781fd38f8bf5491da6948901a1d5
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925732"
---
# <a name="how-to-specify-the-security-context-for-services"></a>Postupy: Určení kontextu zabezpečení pro služby
Ve výchozím nastavení se služby spouštějí v jiném kontextu zabezpečení než přihlášený uživatel. Služby jsou spuštěny v kontextu výchozího systémového účtu, který je volán s `LocalSystem` různými přístupovými oprávněními k systémovým prostředkům, než uživatel. Toto chování můžete změnit tak, aby určovalo jiný uživatelský účet, pod kterým by měla služba běžet.  
  
 Kontext zabezpečení můžete nastavit tak, že budete pracovat s <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> vlastností procesu, ve kterém je služba spuštěná. Tato vlastnost umožňuje nastavit službu na jeden ze čtyř typů účtů:  
  
- `User`, což způsobí, že systém vyzve k zadání platného uživatelského jména a hesla, když je služba nainstalovaná a běží v kontextu účtu zadaného jedním uživatelem v síti.  
  
- `LocalService`, který běží v kontextu účtu, který funguje jako Neprivilegovaný uživatel v místním počítači, a prezentuje anonymní přihlašovací údaje pro všechny vzdálené servery.  
  
- `LocalSystem`, které běží v kontextu účtu, který poskytuje rozsáhlá místní oprávnění, a prezentuje přihlašovací údaje počítače na jakémkoli vzdáleném serveru.  
  
- `NetworkService`, která běží v kontextu účtu, který funguje jako Neprivilegovaný uživatel v místním počítači, a prezentuje přihlašovací údaje počítače k jakémukoli vzdálenému serveru.  
  
 Další informace najdete v tématu <xref:System.ServiceProcess.ServiceAccount> výčet.  
  
### <a name="to-specify-the-security-context-for-a-service"></a>Určení kontextu zabezpečení pro službu  
  
1. Po vytvoření služby přidejte pro ni potřebné instalační programy. Další informace najdete v tématu [Postup: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md).  
  
2. V Návrháři přejděte ke `ProjectInstaller` třídě a klikněte na instalační program procesu služby pro službu, se kterou pracujete.  
  
    > [!NOTE]
    > Pro každou aplikaci služby je ve třídě k dispozici alespoň dvě součásti instalace `ProjectInstaller` – jeden, který nainstaluje procesy pro všechny služby v projektu, a jeden instalační program pro každou službu, kterou aplikace obsahuje. V této instanci chcete vybrat <xref:System.ServiceProcess.ServiceProcessInstaller> .  
  
3. V okně **vlastnosti** nastavte na <xref:System.ServiceProcess.ServiceProcessInstaller.Account%2A> odpovídající hodnotu.  
  
## <a name="see-also"></a>Viz také

- [Představení aplikací spouštěných jako služby systému Windows](introduction-to-windows-service-applications.md)
- [Postupy: Přidání instalačních programů do aplikace služby](how-to-add-installers-to-your-service-application.md)
- [Postupy: Vytváření služeb systému Windows](how-to-create-windows-services.md)
