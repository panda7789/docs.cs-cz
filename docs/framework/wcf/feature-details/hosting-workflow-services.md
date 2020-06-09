---
title: Hostování služeb pracovních postupů
ms.date: 03/30/2017
ms.assetid: 2d55217e-8697-4113-94ce-10b60863342e
ms.openlocfilehash: 908ef7ebb9bfb1e2c49d96e41c0df1d843c0454d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597277"
---
# <a name="hosting-workflow-services"></a>Hostování služeb pracovních postupů

Služba pracovního postupu musí být hostovaná, aby reagovala na příchozí zprávy. Služby pracovních postupů používají infrastrukturu zasílání zpráv WCF a jsou proto hostované podobným způsobem. Podobně jako služby WCF může být služba pracovních postupů hostovaná v jakékoli spravované aplikaci, v části Internetová informační služba (IIS) nebo v části aktivační služba procesů systému Windows (WAS). Služby pracovních postupů je navíc možné hostovat v rámci technologie Windows Server App Fabric. Další informace o Windows Server App Fabric najdete v [dokumentaci k Windows serveru App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)), [funkcích hostování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))a [konceptům hostování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)). Další informace o různých způsobech hostování služeb WCF najdete v tématu [hostingové služby](../hosting-services.md).

## <a name="hosting-in-a-managed-application"></a>Hostování ve spravované aplikaci
 Chcete-li hostovat službu pracovního postupu ve spravované aplikaci, použijte <xref:System.ServiceModel.Activities.WorkflowServiceHost> třídu. <xref:System.ServiceModel.Activities.WorkflowServiceHost>Konstruktor umožňuje zadat instanci služby pracovního postupu typu Singleton, definici služby pracovního postupu nebo aktivitu, která používá aktivity zasílání zpráv pracovního postupu. Volání <xref:System.ServiceModel.Channels.CommunicationObject.Open%2A> způsobí, že služba začne naslouchat příchozím zprávám.

## <a name="hosting-under-iis-or-was"></a>Hostování v rámci služby IIS nebo WAS
 Hostování služby pracovního postupu v rámci služby IIS nebo WAS zahrnuje vytvoření virtuálního adresáře a umístění souborů ve virtuálním adresáři, který definuje službu a její chování. Při hostování služby pracovního postupu v rámci služby IIS nebo má několik možností:

- Umístěte soubor. xamlx, který definuje službu pracovního postupu ve virtuálním adresáři IIS/, spolu se souborem Web. config, který určuje chování služby, koncové body a další prvky konfigurace.

- Umístěte soubor. xamlx, který definuje službu pracovního postupu ve virtuálním adresáři IIS/. Soubor. xamlx určuje koncové body, které mají být vystavení. Koncové body jsou zadány v `WorkflowService.Endpoints` prvku, jak je znázorněno v následujícím příkladu.

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
    > Chování nelze zadat v souboru. xamlx, takže pokud potřebujete zadat nastavení chování, je nutné použít soubor Web. config.

- Umístěte soubor. xamlx, který definuje službu pracovního postupu ve virtuálním adresáři IIS/. Kromě toho umístěte soubor. svc do virtuálního adresáře. Soubor. svc umožňuje zadat vlastní objekt pro vytváření hostitele webové služby, použít vlastní chování nebo načíst konfiguraci z vlastního umístění.

- Umístěte sestavení do virtuálního adresáře IIS/WAS, který obsahuje aktivitu, která používá aktivity zasílání zpráv WCF.

 Soubor. xamlx, který definuje službu pracovního postupu, musí obsahovat `Service` kořenový prvek> <nebo kořenový element, který obsahuje jakýkoli typ odvozený z <xref:System.Workflow.ComponentModel.Activity> . Při použití šablony aktivity aplikace Visual Studio je vytvořen soubor. xamlx. Při použití šablony služby pracovního postupu WCF se vytvoří soubor. xamlx.

## <a name="hosting-workflow-services-under-windows-server-app-fabric"></a>Hostování služeb pracovních postupů v rámci Windows Server App Fabric
 Hostování služby pracovního postupu v rámci technologie Windows Server App Fabric je prováděno stejným způsobem jako hostitelská služba IIS/WAS. Jediným rozdílem je skutečnost, že je nainstalováno Windows Server App Fabric. Windows Server App Fabric nabízí nástroje, které se přidají do Internetová informační služba Manageru, a také rutin PowerShellu. Tyto nástroje zjednodušují nasazení, správu a sledování služeb pracovních postupů a služeb WCF.

## <a name="referencing-custom-activities"></a>Odkazování na vlastní aktivity
 Odkazy na vlastní aktivity musí být přidány do> <`Assemblies` v části <`System.Web.Compilation`>, aby byly načteny do domény aplikace a deserializace jazyka XAML je schopna najít typy. Tato nastavení se dají provést na úrovni aplikace nebo v kořenovém souboru Web. config, pokud se nastavení mají použít pro všechny aplikace v počítači.

## <a name="deployment"></a>Nasazení
 Nástroj pro nasazení webu byl vytvořen za účelem usnadnění úlohy nasazení. Nástroj umožňuje migrovat aplikace mezi službami IIS 6,0 a IIS 7,0, synchronizovat serverové farmy a zabalit, archivovat a nasazovat webové aplikace. Další informace najdete v tématu [Nástroj pro nasazení společnosti Microsoft](https://go.microsoft.com/fwlink/?LinkId=178690).

## <a name="see-also"></a>Viz také

- [Interní informace o hostiteli služby pracovního postupu](workflow-service-host-internals.md)
- [Konfigurace třídy WorkflowServiceHost](configuring-workflowservicehost.md)
