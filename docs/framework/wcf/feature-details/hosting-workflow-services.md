---
title: Hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: c933fd2bd46588ccd5c6115fbc2efca72bfadca4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855865"
---
# <a name="hosting-workflow-services"></a>Hostování služeb pracovních postupů
Služba pracovního postupu musí být hostovaný, aby se reagovat na příchozí zprávy. Služby pracovních postupů pomocí infrastruktury přenosu zpráv WCF a proto hostované podobným způsobem. Stejně jako služby WCF služby pracovních postupů je možné hostovat ve spravované aplikaci, v rámci Internetové informační služby (IIS) nebo v rámci služby pro aktivační proces Windows (WAS). Kromě toho je možné hostovat služby pracovních postupů v rámci Windows Server App Fabric. Další informace o systému Windows Server App Fabric najdete v části [dokumentace ke službě Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=193037), [funkce hostování AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494), a [AppFabric hostování koncepty](https://go.microsoft.com/fwlink/?LinkId=196495). Další informace o různých způsobech hostitele WCF služeb najdete v tématu [hostování služeb](../../../../docs/framework/wcf/hosting-services.md).

## <a name="hosting-in-a-managed-application"></a>Hostování ve spravované aplikaci
 K hostování služby pracovního postupu ve spravované aplikaci, použijte <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídy. <xref:System.ServiceModel.Activities.WorkflowServiceHost> Konstruktor umožňuje zadat instanci pracovního postupu služby typu singleton, definice pracovního postupu služby nebo aktivitou, která používá zasílání zpráv aktivity pracovního postupu. Volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> způsobí, že služba započít naslouchání pro příchozí zprávy.

## <a name="hosting-under-iis-or-was"></a>Hostování v rámci služby IIS nebo WAS
 Hostování služby pracovního procesu v rámci služby IIS nebo WAS zahrnuje vytvoření virtuálního adresáře a umístění souborů do virtuálního adresáře, které definují službě a její chování. Při hostování služby pracovního procesu v rámci služby IIS nebo WAS zde je několik možností:

- Umístíte .xamlx soubor, který definuje službu pracovní postup do IIS / WAS virtuální adresář spolu s souboru Web.config, který určuje chování služby, koncové body a další prvky konfigurace.

- Umístíte .xamlx soubor, který definuje službu pracovní postup do IIS / WAS virtuální adresář. Soubor .xamlx určuje koncových bodů ke zveřejnění. Koncové body jsou uvedeny v `WorkflowService.Endpoints` elementu, jak je znázorněno v následujícím příkladu.

    ```xml
    <WorkflowService xmlns="http://schemas.microsoft.com/netfx/2009/xaml/servicemodel"  xmlns:p1="http://schemas.microsoft.com/netfx/2009/xaml/activities" xmlns:sad="clr-namespace:System.Activities.Debugger;assembly=System.Activities" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml">
      <WorkflowService.Endpoints>
        <Endpoint ServiceContractName="IWorkFlowEchoService" AddressUri="">
          <Endpoint.Binding>
            <BasicHttpBinding />
          </Endpoint.Binding>
        </Endpoint>
      </WorkflowService.Endpoints>
    <!-- ... -->
    </WorkflowService>
    ```

    > [!NOTE]
    > Chování nelze zadat v souboru .xamlx, takže pokud je třeba zadat nastavení chování je nutné použít souboru Web.config.

- Umístíte .xamlx soubor, který definuje službu pracovní postup do IIS / WAS virtuální adresář. Kromě toho umístíte soubor .svc ve virtuálním adresáři. Souboru SVC umožňuje zadat vlastní vytváření hostitele webové služby, použít vlastní chování nebo zavést konfiguraci z vlastního umístění.

- Sestavení umístěte do služby IIS / byla virtuální adresář, který obsahuje aktivitu, která používá WCF zasílání zpráv aktivity.

 Musí obsahovat .xamlx soubor, který definuje služby pracovních postupů <`Service`> kořenový element nebo kořenový element, který obsahuje libovolného typu odvozeného z <xref:System.Workflow.ComponentModel.Activity>. Při použití šablony aktivit sady Visual Studio, je vytvořen soubor .xamlx. Při použití šablony služby pracovního postupu WCF, se vytvoří soubor .xamlx.

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Hostování služeb pracovních postupů v rámci Windows Server App Fabric
 Hostování služby pracovního procesu v rámci Windows Server App Fabric se provádí stejným způsobem, který hostuje v rámci služby IIS nebo WAS. Jediným rozdílem je skutečnost, že je nainstalovaný Windows Server App Fabric. Windows Server App Fabric nabízí nástroje, které jsou přidány do Správce Internetové informační služby, jakož i rutiny prostředí PowerShell. Tyto nástroje zjednodušit nasazení, správě a sledování pracovního postupu služby a služby WCF.

## <a name="referencing-custom-activities"></a>Odkazování na vlastní aktivity
 Odkazy na vlastní aktivity musí být přidané do <`Assemblies`> v oddílu <`System.Web.Compilation`> tak, aby se načteno do domény aplikace a deserializátor XAML je schopen najít typy. Tato nastavení lze provést na úrovni aplikace nebo v kořenovém souboru Web.config, pokud nastavení bude použito na všechny aplikace na počítači.

## <a name="deployment"></a>Nasazení
 Nástroj nasazení webu byla vytvořená za účelem usnadnění práce pro nasazení. Nástroj umožňuje migrace aplikací mezi službami IIS 6.0 a IIS 7.0, synchronizace serverové farmy a balíčků, archivování a nasazování webových aplikací. Další informace najdete v tématu [nástroj pro nasazení MS](https://go.microsoft.com/fwlink/?LinkId=178690).

## <a name="see-also"></a>Viz také:

- [Interní informace o hostiteli služby pracovního postupu](../../../../docs/framework/wcf/feature-details/workflow-service-host-internals.md)
- [Konfigurace třídy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/configuring-workflowservicehost.md)