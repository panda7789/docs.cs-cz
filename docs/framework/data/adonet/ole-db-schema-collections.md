---
title: Kolekce schémat OLE DB
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59164681"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="28ec4-102">Kolekce schémat OLE DB</span><span class="sxs-lookup"><span data-stu-id="28ec4-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="28ec4-103">Tato část popisuje kolekci podpora schématu pro zprostředkovatele OLE DB pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="28ec4-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="28ec4-104">Zprostředkovatel Microsoft SQL serveru OLE DB</span><span class="sxs-lookup"><span data-stu-id="28ec4-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="28ec4-105">Microsoft SQL Server OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="28ec4-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="28ec4-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="28ec4-106">Tables</span></span>  
  
-   <span data-ttu-id="28ec4-107">Sloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-107">Columns</span></span>  
  
-   <span data-ttu-id="28ec4-108">Procedury</span><span class="sxs-lookup"><span data-stu-id="28ec4-108">Procedures</span></span>  
  
-   <span data-ttu-id="28ec4-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="28ec4-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="28ec4-110">Katalog</span><span class="sxs-lookup"><span data-stu-id="28ec4-110">Catalog</span></span>  
  
-   <span data-ttu-id="28ec4-111">Indexy</span><span class="sxs-lookup"><span data-stu-id="28ec4-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="28ec4-112">Tabulky</span><span class="sxs-lookup"><span data-stu-id="28ec4-112">Tables</span></span>  
  
|<span data-ttu-id="28ec4-113">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-113">ColumnName</span></span>|<span data-ttu-id="28ec4-114">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-115">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-116">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-116">String</span></span>|  
|<span data-ttu-id="28ec4-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-118">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-118">String</span></span>|  
|<span data-ttu-id="28ec4-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-119">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-120">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-120">String</span></span>|  
|<span data-ttu-id="28ec4-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-121">TABLE_TYPE</span></span>|<span data-ttu-id="28ec4-122">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-122">String</span></span>|  
|<span data-ttu-id="28ec4-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-123">TABLE_GUID</span></span>|<span data-ttu-id="28ec4-124">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-124">Guid</span></span>|  
|<span data-ttu-id="28ec4-125">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-125">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-126">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-126">String</span></span>|  
|<span data-ttu-id="28ec4-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-127">TABLE_PROPID</span></span>|<span data-ttu-id="28ec4-128">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-128">Int64</span></span>|  
|<span data-ttu-id="28ec4-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="28ec4-129">DATE_CREATED</span></span>|<span data-ttu-id="28ec4-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-130">DateTime</span></span>|  
|<span data-ttu-id="28ec4-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="28ec4-131">DATE_MODIFIED</span></span>|<span data-ttu-id="28ec4-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="28ec4-133">Sloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-133">Columns</span></span>  
  
|<span data-ttu-id="28ec4-134">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-134">ColumnName</span></span>|<span data-ttu-id="28ec4-135">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-136">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-137">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-137">String</span></span>|  
|<span data-ttu-id="28ec4-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-139">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-139">String</span></span>|  
|<span data-ttu-id="28ec4-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-140">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-141">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-141">String</span></span>|  
|<span data-ttu-id="28ec4-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-142">COLUMN_NAME</span></span>|<span data-ttu-id="28ec4-143">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-143">String</span></span>|  
|<span data-ttu-id="28ec4-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-144">COLUMN_GUID</span></span>|<span data-ttu-id="28ec4-145">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-145">Guid</span></span>|  
|<span data-ttu-id="28ec4-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-146">COLUMN_PROPID</span></span>|<span data-ttu-id="28ec4-147">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-147">Int64</span></span>|  
|<span data-ttu-id="28ec4-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="28ec4-149">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-149">Int64</span></span>|  
|<span data-ttu-id="28ec4-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="28ec4-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="28ec4-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-151">Boolean</span></span>|  
|<span data-ttu-id="28ec4-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="28ec4-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="28ec4-153">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-153">String</span></span>|  
|<span data-ttu-id="28ec4-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="28ec4-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="28ec4-155">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-155">Int64</span></span>|  
|<span data-ttu-id="28ec4-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="28ec4-156">IS_NULLABLE</span></span>|<span data-ttu-id="28ec4-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-157">Boolean</span></span>|  
|<span data-ttu-id="28ec4-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-158">DATA_TYPE</span></span>|<span data-ttu-id="28ec4-159">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-159">Int32</span></span>|  
|<span data-ttu-id="28ec4-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-160">TYPE_GUID</span></span>|<span data-ttu-id="28ec4-161">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-161">Guid</span></span>|  
|<span data-ttu-id="28ec4-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="28ec4-163">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-163">Int64</span></span>|  
|<span data-ttu-id="28ec4-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="28ec4-165">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-165">Int64</span></span>|  
|<span data-ttu-id="28ec4-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="28ec4-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="28ec4-167">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-167">Int32</span></span>|  
|<span data-ttu-id="28ec4-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="28ec4-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="28ec4-169">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-169">Int16</span></span>|  
|<span data-ttu-id="28ec4-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="28ec4-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="28ec4-171">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-171">Int64</span></span>|  
|<span data-ttu-id="28ec4-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="28ec4-173">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-173">String</span></span>|  
|<span data-ttu-id="28ec4-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="28ec4-175">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-175">String</span></span>|  
|<span data-ttu-id="28ec4-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="28ec4-177">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-177">String</span></span>|  
|<span data-ttu-id="28ec4-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="28ec4-179">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-179">String</span></span>|  
|<span data-ttu-id="28ec4-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="28ec4-181">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-181">String</span></span>|  
|<span data-ttu-id="28ec4-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-182">COLLATION_NAME</span></span>|<span data-ttu-id="28ec4-183">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-183">String</span></span>|  
|<span data-ttu-id="28ec4-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="28ec4-185">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-185">String</span></span>|  
|<span data-ttu-id="28ec4-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="28ec4-187">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-187">String</span></span>|  
|<span data-ttu-id="28ec4-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-188">DOMAIN_NAME</span></span>|<span data-ttu-id="28ec4-189">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-189">String</span></span>|  
|<span data-ttu-id="28ec4-190">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-190">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-191">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-191">String</span></span>|  
|<span data-ttu-id="28ec4-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="28ec4-192">COLUMN_LCID</span></span>|<span data-ttu-id="28ec4-193">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-193">Int32</span></span>|  
|<span data-ttu-id="28ec4-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="28ec4-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="28ec4-195">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-195">Int32</span></span>|  
|<span data-ttu-id="28ec4-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="28ec4-196">COLUMN_SORTID</span></span>|<span data-ttu-id="28ec4-197">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-197">Int32</span></span>|  
|<span data-ttu-id="28ec4-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="28ec4-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="28ec4-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="28ec4-199">Byte[]</span></span>|  
|<span data-ttu-id="28ec4-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="28ec4-200">IS_COMPUTED</span></span>|<span data-ttu-id="28ec4-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="28ec4-202">Procedury</span><span class="sxs-lookup"><span data-stu-id="28ec4-202">Procedures</span></span>  
  
|<span data-ttu-id="28ec4-203">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-203">ColumnName</span></span>|<span data-ttu-id="28ec4-204">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="28ec4-206">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-206">String</span></span>|  
|<span data-ttu-id="28ec4-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="28ec4-208">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-208">String</span></span>|  
|<span data-ttu-id="28ec4-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="28ec4-210">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-210">String</span></span>|  
|<span data-ttu-id="28ec4-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="28ec4-212">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-212">Int16</span></span>|  
|<span data-ttu-id="28ec4-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="28ec4-214">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-214">String</span></span>|  
|<span data-ttu-id="28ec4-215">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-215">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-216">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-216">String</span></span>|  
|<span data-ttu-id="28ec4-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="28ec4-217">DATE_CREATED</span></span>|<span data-ttu-id="28ec4-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-218">DateTime</span></span>|  
|<span data-ttu-id="28ec4-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="28ec4-219">DATE_MODIFIED</span></span>|<span data-ttu-id="28ec4-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="28ec4-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="28ec4-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="28ec4-222">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-222">ColumnName</span></span>|<span data-ttu-id="28ec4-223">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="28ec4-225">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-225">String</span></span>|  
|<span data-ttu-id="28ec4-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="28ec4-227">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-227">String</span></span>|  
|<span data-ttu-id="28ec4-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="28ec4-229">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-229">String</span></span>|  
|<span data-ttu-id="28ec4-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-230">PARAMETER_NAME</span></span>|<span data-ttu-id="28ec4-231">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-231">String</span></span>|  
|<span data-ttu-id="28ec4-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="28ec4-233">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-233">Int32</span></span>|  
|<span data-ttu-id="28ec4-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="28ec4-235">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-235">Int32</span></span>|  
|<span data-ttu-id="28ec4-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="28ec4-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="28ec4-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-237">Boolean</span></span>|  
|<span data-ttu-id="28ec4-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="28ec4-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="28ec4-239">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-239">String</span></span>|  
|<span data-ttu-id="28ec4-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="28ec4-240">IS_NULLABLE</span></span>|<span data-ttu-id="28ec4-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-241">Boolean</span></span>|  
|<span data-ttu-id="28ec4-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-242">DATA_TYPE</span></span>|<span data-ttu-id="28ec4-243">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-243">Int32</span></span>|  
|<span data-ttu-id="28ec4-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="28ec4-245">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-245">Int64</span></span>|  
|<span data-ttu-id="28ec4-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="28ec4-247">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-247">Int64</span></span>|  
|<span data-ttu-id="28ec4-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="28ec4-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="28ec4-249">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-249">Int32</span></span>|  
|<span data-ttu-id="28ec4-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="28ec4-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="28ec4-251">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-251">Int16</span></span>|  
|<span data-ttu-id="28ec4-252">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-252">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-253">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-253">String</span></span>|  
|<span data-ttu-id="28ec4-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-254">TYPE_NAME</span></span>|<span data-ttu-id="28ec4-255">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-255">String</span></span>|  
|<span data-ttu-id="28ec4-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="28ec4-257">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="28ec4-258">Katalog</span><span class="sxs-lookup"><span data-stu-id="28ec4-258">Catalog</span></span>  
  
|<span data-ttu-id="28ec4-259">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-259">ColumnName</span></span>|<span data-ttu-id="28ec4-260">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-261">CATALOG_NAME</span></span>|<span data-ttu-id="28ec4-262">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-262">String</span></span>|  
|<span data-ttu-id="28ec4-263">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-263">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-264">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="28ec4-265">Indexy</span><span class="sxs-lookup"><span data-stu-id="28ec4-265">Indexes</span></span>  
  
|<span data-ttu-id="28ec4-266">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-266">ColumnName</span></span>|<span data-ttu-id="28ec4-267">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-268">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-269">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-269">String</span></span>|  
|<span data-ttu-id="28ec4-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-271">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-271">String</span></span>|  
|<span data-ttu-id="28ec4-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-272">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-273">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-273">String</span></span>|  
|<span data-ttu-id="28ec4-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-274">INDEX_CATALOG</span></span>|<span data-ttu-id="28ec4-275">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-275">String</span></span>|  
|<span data-ttu-id="28ec4-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="28ec4-277">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-277">String</span></span>|  
|<span data-ttu-id="28ec4-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-278">INDEX_NAME</span></span>|<span data-ttu-id="28ec4-279">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-279">String</span></span>|  
|<span data-ttu-id="28ec4-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="28ec4-280">PRIMARY_KEY</span></span>|<span data-ttu-id="28ec4-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-281">Boolean</span></span>|  
|<span data-ttu-id="28ec4-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="28ec4-282">UNIQUE</span></span>|<span data-ttu-id="28ec4-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-283">Boolean</span></span>|  
|<span data-ttu-id="28ec4-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="28ec4-284">CLUSTERED</span></span>|<span data-ttu-id="28ec4-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-285">Boolean</span></span>|  
|<span data-ttu-id="28ec4-286">TYP</span><span class="sxs-lookup"><span data-stu-id="28ec4-286">TYPE</span></span>|<span data-ttu-id="28ec4-287">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-287">Int32</span></span>|  
|<span data-ttu-id="28ec4-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="28ec4-288">FILL_FACTOR</span></span>|<span data-ttu-id="28ec4-289">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-289">Int32</span></span>|  
|<span data-ttu-id="28ec4-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="28ec4-290">INITIAL_SIZE</span></span>|<span data-ttu-id="28ec4-291">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-291">Int32</span></span>|  
|<span data-ttu-id="28ec4-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="28ec4-292">NULLS</span></span>|<span data-ttu-id="28ec4-293">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-293">Int32</span></span>|  
|<span data-ttu-id="28ec4-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="28ec4-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="28ec4-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-295">Boolean</span></span>|  
|<span data-ttu-id="28ec4-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="28ec4-296">AUTO_UPDATE</span></span>|<span data-ttu-id="28ec4-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-297">Boolean</span></span>|  
|<span data-ttu-id="28ec4-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="28ec4-298">NULL_COLLATION</span></span>|<span data-ttu-id="28ec4-299">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-299">Int32</span></span>|  
|<span data-ttu-id="28ec4-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="28ec4-301">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-301">Int64</span></span>|  
|<span data-ttu-id="28ec4-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-302">COLUMN_NAME</span></span>|<span data-ttu-id="28ec4-303">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-303">String</span></span>|  
|<span data-ttu-id="28ec4-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-304">COLUMN_GUID</span></span>|<span data-ttu-id="28ec4-305">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-305">Guid</span></span>|  
|<span data-ttu-id="28ec4-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-306">COLUMN_PROPID</span></span>|<span data-ttu-id="28ec4-307">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-307">Int64</span></span>|  
|<span data-ttu-id="28ec4-308">KOLACE</span><span class="sxs-lookup"><span data-stu-id="28ec4-308">COLLATION</span></span>|<span data-ttu-id="28ec4-309">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-309">Int16</span></span>|  
|<span data-ttu-id="28ec4-310">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="28ec4-310">CARDINALITY</span></span>|<span data-ttu-id="28ec4-311">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="28ec4-311">Decimal</span></span>|  
|<span data-ttu-id="28ec4-312">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="28ec4-312">PAGES</span></span>|<span data-ttu-id="28ec4-313">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-313">Int32</span></span>|  
|<span data-ttu-id="28ec4-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-314">FILTER_CONDITION</span></span>|<span data-ttu-id="28ec4-315">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-315">String</span></span>|  
|<span data-ttu-id="28ec4-316">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="28ec4-316">INTEGRATED</span></span>|<span data-ttu-id="28ec4-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="28ec4-318">Zprostředkovatel OLE DB Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="28ec4-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="28ec4-319">Oracle OLE DB ovladač Microsoft podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="28ec4-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="28ec4-320">Tabulky</span><span class="sxs-lookup"><span data-stu-id="28ec4-320">Tables</span></span>  
  
-   <span data-ttu-id="28ec4-321">Sloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-321">Columns</span></span>  
  
-   <span data-ttu-id="28ec4-322">Procedury</span><span class="sxs-lookup"><span data-stu-id="28ec4-322">Procedures</span></span>  
  
-   <span data-ttu-id="28ec4-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="28ec4-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="28ec4-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="28ec4-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="28ec4-325">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="28ec4-325">Views</span></span>  
  
-   <span data-ttu-id="28ec4-326">Indexy</span><span class="sxs-lookup"><span data-stu-id="28ec4-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="28ec4-327">Tabulky</span><span class="sxs-lookup"><span data-stu-id="28ec4-327">Tables</span></span>  
  
|<span data-ttu-id="28ec4-328">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-328">ColumnName</span></span>|<span data-ttu-id="28ec4-329">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-330">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-331">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-331">String</span></span>|  
|<span data-ttu-id="28ec4-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-333">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-333">String</span></span>|  
|<span data-ttu-id="28ec4-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-334">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-335">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-335">String</span></span>|  
|<span data-ttu-id="28ec4-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-336">TABLE_TYPE</span></span>|<span data-ttu-id="28ec4-337">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-337">String</span></span>|  
|<span data-ttu-id="28ec4-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-338">TABLE_GUID</span></span>|<span data-ttu-id="28ec4-339">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-339">Guid</span></span>|  
|<span data-ttu-id="28ec4-340">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-340">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-341">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-341">String</span></span>|  
|<span data-ttu-id="28ec4-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-342">TABLE_PROPID</span></span>|<span data-ttu-id="28ec4-343">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-343">Int64</span></span>|  
|<span data-ttu-id="28ec4-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="28ec4-344">DATE_CREATED</span></span>|<span data-ttu-id="28ec4-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-345">DateTime</span></span>|  
|<span data-ttu-id="28ec4-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="28ec4-346">DATE_MODIFIED</span></span>|<span data-ttu-id="28ec4-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="28ec4-348">Sloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-348">Columns</span></span>  
  
|<span data-ttu-id="28ec4-349">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-349">ColumnName</span></span>|<span data-ttu-id="28ec4-350">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-351">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-352">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-352">String</span></span>|  
|<span data-ttu-id="28ec4-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-354">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-354">String</span></span>|  
|<span data-ttu-id="28ec4-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-355">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-356">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-356">String</span></span>|  
|<span data-ttu-id="28ec4-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-357">COLUMN_NAME</span></span>|<span data-ttu-id="28ec4-358">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-358">String</span></span>|  
|<span data-ttu-id="28ec4-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-359">COLUMN_GUID</span></span>|<span data-ttu-id="28ec4-360">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-360">Guid</span></span>|  
|<span data-ttu-id="28ec4-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-361">COLUMN_PROPID</span></span>|<span data-ttu-id="28ec4-362">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-362">Int64</span></span>|  
|<span data-ttu-id="28ec4-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="28ec4-364">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-364">Int64</span></span>|  
|<span data-ttu-id="28ec4-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="28ec4-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="28ec4-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-366">Boolean</span></span>|  
|<span data-ttu-id="28ec4-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="28ec4-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="28ec4-368">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-368">String</span></span>|  
|<span data-ttu-id="28ec4-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="28ec4-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="28ec4-370">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-370">Int64</span></span>|  
|<span data-ttu-id="28ec4-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="28ec4-371">IS_NULLABLE</span></span>|<span data-ttu-id="28ec4-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-372">Boolean</span></span>|  
|<span data-ttu-id="28ec4-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-373">DATA_TYPE</span></span>|<span data-ttu-id="28ec4-374">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-374">Int32</span></span>|  
|<span data-ttu-id="28ec4-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-375">TYPE_GUID</span></span>|<span data-ttu-id="28ec4-376">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-376">Guid</span></span>|  
|<span data-ttu-id="28ec4-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="28ec4-378">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-378">Int64</span></span>|  
|<span data-ttu-id="28ec4-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="28ec4-380">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-380">Int64</span></span>|  
|<span data-ttu-id="28ec4-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="28ec4-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="28ec4-382">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-382">Int32</span></span>|  
|<span data-ttu-id="28ec4-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="28ec4-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="28ec4-384">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-384">Int16</span></span>|  
|<span data-ttu-id="28ec4-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="28ec4-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="28ec4-386">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-386">Int64</span></span>|  
|<span data-ttu-id="28ec4-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="28ec4-388">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-388">String</span></span>|  
|<span data-ttu-id="28ec4-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="28ec4-390">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-390">String</span></span>|  
|<span data-ttu-id="28ec4-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="28ec4-392">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-392">String</span></span>|  
|<span data-ttu-id="28ec4-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="28ec4-394">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-394">String</span></span>|  
|<span data-ttu-id="28ec4-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="28ec4-396">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-396">String</span></span>|  
|<span data-ttu-id="28ec4-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-397">COLLATION_NAME</span></span>|<span data-ttu-id="28ec4-398">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-398">String</span></span>|  
|<span data-ttu-id="28ec4-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="28ec4-400">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-400">String</span></span>|  
|<span data-ttu-id="28ec4-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="28ec4-402">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-402">String</span></span>|  
|<span data-ttu-id="28ec4-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-403">DOMAIN_NAME</span></span>|<span data-ttu-id="28ec4-404">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-404">String</span></span>|  
|<span data-ttu-id="28ec4-405">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-405">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-406">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="28ec4-407">Procedury</span><span class="sxs-lookup"><span data-stu-id="28ec4-407">Procedures</span></span>  
  
|<span data-ttu-id="28ec4-408">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-408">ColumnName</span></span>|<span data-ttu-id="28ec4-409">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="28ec4-411">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-411">String</span></span>|  
|<span data-ttu-id="28ec4-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="28ec4-413">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-413">String</span></span>|  
|<span data-ttu-id="28ec4-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="28ec4-415">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-415">String</span></span>|  
|<span data-ttu-id="28ec4-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="28ec4-417">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-417">Int16</span></span>|  
|<span data-ttu-id="28ec4-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="28ec4-419">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-419">String</span></span>|  
|<span data-ttu-id="28ec4-420">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-420">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-421">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-421">String</span></span>|  
|<span data-ttu-id="28ec4-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="28ec4-422">DATE_CREATED</span></span>|<span data-ttu-id="28ec4-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-423">DateTime</span></span>|  
|<span data-ttu-id="28ec4-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="28ec4-424">DATE_MODIFIED</span></span>|<span data-ttu-id="28ec4-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="28ec4-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="28ec4-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="28ec4-427">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-427">ColumnName</span></span>|<span data-ttu-id="28ec4-428">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="28ec4-430">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-430">String</span></span>|  
|<span data-ttu-id="28ec4-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="28ec4-432">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-432">String</span></span>|  
|<span data-ttu-id="28ec4-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="28ec4-434">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-434">String</span></span>|  
|<span data-ttu-id="28ec4-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-435">COLUMN_NAME</span></span>|<span data-ttu-id="28ec4-436">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-436">String</span></span>|  
|<span data-ttu-id="28ec4-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-437">COLUMN_GUID</span></span>|<span data-ttu-id="28ec4-438">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-438">Guid</span></span>|  
|<span data-ttu-id="28ec4-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-439">COLUMN_PROPID</span></span>|<span data-ttu-id="28ec4-440">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-440">Int64</span></span>|  
|<span data-ttu-id="28ec4-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="28ec4-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="28ec4-442">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-442">Int64</span></span>|  
|<span data-ttu-id="28ec4-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="28ec4-444">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-444">Int64</span></span>|  
|<span data-ttu-id="28ec4-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="28ec4-445">IS_NULLABLE</span></span>|<span data-ttu-id="28ec4-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-446">Boolean</span></span>|  
|<span data-ttu-id="28ec4-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-447">DATA_TYPE</span></span>|<span data-ttu-id="28ec4-448">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-448">Int32</span></span>|  
|<span data-ttu-id="28ec4-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-449">TYPE_GUID</span></span>|<span data-ttu-id="28ec4-450">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-450">Guid</span></span>|  
|<span data-ttu-id="28ec4-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="28ec4-452">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-452">Int64</span></span>|  
|<span data-ttu-id="28ec4-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="28ec4-454">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-454">Int64</span></span>|  
|<span data-ttu-id="28ec4-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="28ec4-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="28ec4-456">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-456">Int32</span></span>|  
|<span data-ttu-id="28ec4-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="28ec4-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="28ec4-458">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-458">Int16</span></span>|  
|<span data-ttu-id="28ec4-459">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-459">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-460">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-460">String</span></span>|  
|<span data-ttu-id="28ec4-461">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="28ec4-461">OVERLOAD</span></span>|<span data-ttu-id="28ec4-462">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="28ec4-463">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="28ec4-463">Views</span></span>  
  
|<span data-ttu-id="28ec4-464">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-464">ColumnName</span></span>|<span data-ttu-id="28ec4-465">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-466">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-467">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-467">String</span></span>|  
|<span data-ttu-id="28ec4-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-469">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-469">String</span></span>|  
|<span data-ttu-id="28ec4-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-470">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-471">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-471">String</span></span>|  
|<span data-ttu-id="28ec4-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="28ec4-473">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-473">String</span></span>|  
|<span data-ttu-id="28ec4-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="28ec4-474">CHECK_OPTION</span></span>|<span data-ttu-id="28ec4-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-475">Boolean</span></span>|  
|<span data-ttu-id="28ec4-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="28ec4-476">IS_UPDATABLE</span></span>|<span data-ttu-id="28ec4-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-477">Boolean</span></span>|  
|<span data-ttu-id="28ec4-478">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-478">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-479">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-479">String</span></span>|  
|<span data-ttu-id="28ec4-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="28ec4-480">DATE_CREATED</span></span>|<span data-ttu-id="28ec4-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-481">DateTime</span></span>|  
|<span data-ttu-id="28ec4-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="28ec4-482">DATE_MODIFIED</span></span>|<span data-ttu-id="28ec4-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="28ec4-484">Indexy</span><span class="sxs-lookup"><span data-stu-id="28ec4-484">Indexes</span></span>  
  
|<span data-ttu-id="28ec4-485">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-485">ColumnName</span></span>|<span data-ttu-id="28ec4-486">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-487">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-488">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-488">String</span></span>|  
|<span data-ttu-id="28ec4-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-490">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-490">String</span></span>|  
|<span data-ttu-id="28ec4-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-491">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-492">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-492">String</span></span>|  
|<span data-ttu-id="28ec4-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-493">INDEX_CATALOG</span></span>|<span data-ttu-id="28ec4-494">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-494">String</span></span>|  
|<span data-ttu-id="28ec4-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="28ec4-496">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-496">String</span></span>|  
|<span data-ttu-id="28ec4-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-497">INDEX_NAME</span></span>|<span data-ttu-id="28ec4-498">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-498">String</span></span>|  
|<span data-ttu-id="28ec4-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="28ec4-499">PRIMARY_KEY</span></span>|<span data-ttu-id="28ec4-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-500">Boolean</span></span>|  
|<span data-ttu-id="28ec4-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="28ec4-501">UNIQUE</span></span>|<span data-ttu-id="28ec4-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-502">Boolean</span></span>|  
|<span data-ttu-id="28ec4-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="28ec4-503">CLUSTERED</span></span>|<span data-ttu-id="28ec4-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-504">Boolean</span></span>|  
|<span data-ttu-id="28ec4-505">TYP</span><span class="sxs-lookup"><span data-stu-id="28ec4-505">TYPE</span></span>|<span data-ttu-id="28ec4-506">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-506">Int32</span></span>|  
|<span data-ttu-id="28ec4-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="28ec4-507">FILL_FACTOR</span></span>|<span data-ttu-id="28ec4-508">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-508">Int32</span></span>|  
|<span data-ttu-id="28ec4-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="28ec4-509">INITIAL_SIZE</span></span>|<span data-ttu-id="28ec4-510">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-510">Int32</span></span>|  
|<span data-ttu-id="28ec4-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="28ec4-511">NULLS</span></span>|<span data-ttu-id="28ec4-512">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-512">Int32</span></span>|  
|<span data-ttu-id="28ec4-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="28ec4-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="28ec4-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-514">Boolean</span></span>|  
|<span data-ttu-id="28ec4-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="28ec4-515">AUTO_UPDATE</span></span>|<span data-ttu-id="28ec4-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-516">Boolean</span></span>|  
|<span data-ttu-id="28ec4-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="28ec4-517">NULL_COLLATION</span></span>|<span data-ttu-id="28ec4-518">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-518">Int32</span></span>|  
|<span data-ttu-id="28ec4-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="28ec4-520">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-520">Int64</span></span>|  
|<span data-ttu-id="28ec4-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-521">COLUMN_NAME</span></span>|<span data-ttu-id="28ec4-522">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-522">String</span></span>|  
|<span data-ttu-id="28ec4-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-523">COLUMN_GUID</span></span>|<span data-ttu-id="28ec4-524">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-524">Guid</span></span>|  
|<span data-ttu-id="28ec4-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-525">COLUMN_PROPID</span></span>|<span data-ttu-id="28ec4-526">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-526">Int64</span></span>|  
|<span data-ttu-id="28ec4-527">KOLACE</span><span class="sxs-lookup"><span data-stu-id="28ec4-527">COLLATION</span></span>|<span data-ttu-id="28ec4-528">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-528">Int16</span></span>|  
|<span data-ttu-id="28ec4-529">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="28ec4-529">CARDINALITY</span></span>|<span data-ttu-id="28ec4-530">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="28ec4-530">Decimal</span></span>|  
|<span data-ttu-id="28ec4-531">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="28ec4-531">PAGES</span></span>|<span data-ttu-id="28ec4-532">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-532">Int32</span></span>|  
|<span data-ttu-id="28ec4-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-533">FILTER_CONDITION</span></span>|<span data-ttu-id="28ec4-534">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-534">String</span></span>|  
|<span data-ttu-id="28ec4-535">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="28ec4-535">INTEGRATED</span></span>|<span data-ttu-id="28ec4-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="28ec4-537">Zprostředkovatel Microsoft Jet OLE DB</span><span class="sxs-lookup"><span data-stu-id="28ec4-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="28ec4-538">Microsoft Jet OLE DB ovladač podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="28ec4-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="28ec4-539">Tabulky</span><span class="sxs-lookup"><span data-stu-id="28ec4-539">Tables</span></span>  
  
-   <span data-ttu-id="28ec4-540">Sloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-540">Columns</span></span>  
  
-   <span data-ttu-id="28ec4-541">Procedury</span><span class="sxs-lookup"><span data-stu-id="28ec4-541">Procedures</span></span>  
  
-   <span data-ttu-id="28ec4-542">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="28ec4-542">Views</span></span>  
  
-   <span data-ttu-id="28ec4-543">Indexy</span><span class="sxs-lookup"><span data-stu-id="28ec4-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="28ec4-544">Tabulky</span><span class="sxs-lookup"><span data-stu-id="28ec4-544">Tables</span></span>  
  
|<span data-ttu-id="28ec4-545">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-545">ColumnName</span></span>|<span data-ttu-id="28ec4-546">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-547">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-548">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-548">String</span></span>|  
|<span data-ttu-id="28ec4-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-550">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-550">String</span></span>|  
|<span data-ttu-id="28ec4-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-551">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-552">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-552">String</span></span>|  
|<span data-ttu-id="28ec4-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-553">TABLE_TYPE</span></span>|<span data-ttu-id="28ec4-554">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-554">String</span></span>|  
|<span data-ttu-id="28ec4-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-555">TABLE_GUID</span></span>|<span data-ttu-id="28ec4-556">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-556">Guid</span></span>|  
|<span data-ttu-id="28ec4-557">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-557">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-558">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-558">String</span></span>|  
|<span data-ttu-id="28ec4-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-559">TABLE_PROPID</span></span>|<span data-ttu-id="28ec4-560">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-560">Int64</span></span>|  
|<span data-ttu-id="28ec4-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="28ec4-561">DATE_CREATED</span></span>|<span data-ttu-id="28ec4-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-562">DateTime</span></span>|  
|<span data-ttu-id="28ec4-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="28ec4-563">DATE_MODIFIED</span></span>|<span data-ttu-id="28ec4-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="28ec4-565">Sloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-565">Columns</span></span>  
  
|<span data-ttu-id="28ec4-566">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-566">ColumnName</span></span>|<span data-ttu-id="28ec4-567">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-568">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-569">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-569">String</span></span>|  
|<span data-ttu-id="28ec4-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-571">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-571">String</span></span>|  
|<span data-ttu-id="28ec4-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-572">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-573">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-573">String</span></span>|  
|<span data-ttu-id="28ec4-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-574">COLUMN_NAME</span></span>|<span data-ttu-id="28ec4-575">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-575">String</span></span>|  
|<span data-ttu-id="28ec4-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-576">COLUMN_GUID</span></span>|<span data-ttu-id="28ec4-577">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-577">Guid</span></span>|  
|<span data-ttu-id="28ec4-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-578">COLUMN_PROPID</span></span>|<span data-ttu-id="28ec4-579">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-579">Int64</span></span>|  
|<span data-ttu-id="28ec4-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="28ec4-581">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-581">Int64</span></span>|  
|<span data-ttu-id="28ec4-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="28ec4-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="28ec4-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-583">Boolean</span></span>|  
|<span data-ttu-id="28ec4-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="28ec4-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="28ec4-585">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-585">String</span></span>|  
|<span data-ttu-id="28ec4-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="28ec4-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="28ec4-587">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-587">Int64</span></span>|  
|<span data-ttu-id="28ec4-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="28ec4-588">IS_NULLABLE</span></span>|<span data-ttu-id="28ec4-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-589">Boolean</span></span>|  
|<span data-ttu-id="28ec4-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-590">DATA_TYPE</span></span>|<span data-ttu-id="28ec4-591">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-591">Int32</span></span>|  
|<span data-ttu-id="28ec4-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-592">TYPE_GUID</span></span>|<span data-ttu-id="28ec4-593">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-593">Guid</span></span>|  
|<span data-ttu-id="28ec4-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="28ec4-595">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-595">Int64</span></span>|  
|<span data-ttu-id="28ec4-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="28ec4-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="28ec4-597">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-597">Int64</span></span>|  
|<span data-ttu-id="28ec4-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="28ec4-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="28ec4-599">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-599">Int32</span></span>|  
|<span data-ttu-id="28ec4-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="28ec4-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="28ec4-601">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-601">Int16</span></span>|  
|<span data-ttu-id="28ec4-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="28ec4-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="28ec4-603">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-603">Int64</span></span>|  
|<span data-ttu-id="28ec4-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="28ec4-605">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-605">String</span></span>|  
|<span data-ttu-id="28ec4-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="28ec4-607">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-607">String</span></span>|  
|<span data-ttu-id="28ec4-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="28ec4-609">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-609">String</span></span>|  
|<span data-ttu-id="28ec4-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="28ec4-611">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-611">String</span></span>|  
|<span data-ttu-id="28ec4-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="28ec4-613">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-613">String</span></span>|  
|<span data-ttu-id="28ec4-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-614">COLLATION_NAME</span></span>|<span data-ttu-id="28ec4-615">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-615">String</span></span>|  
|<span data-ttu-id="28ec4-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="28ec4-617">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-617">String</span></span>|  
|<span data-ttu-id="28ec4-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="28ec4-619">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-619">String</span></span>|  
|<span data-ttu-id="28ec4-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-620">DOMAIN_NAME</span></span>|<span data-ttu-id="28ec4-621">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-621">String</span></span>|  
|<span data-ttu-id="28ec4-622">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-622">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-623">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="28ec4-624">Procedury</span><span class="sxs-lookup"><span data-stu-id="28ec4-624">Procedures</span></span>  
  
|<span data-ttu-id="28ec4-625">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-625">ColumnName</span></span>|<span data-ttu-id="28ec4-626">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="28ec4-628">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-628">String</span></span>|  
|<span data-ttu-id="28ec4-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="28ec4-630">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-630">String</span></span>|  
|<span data-ttu-id="28ec4-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="28ec4-632">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-632">String</span></span>|  
|<span data-ttu-id="28ec4-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="28ec4-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="28ec4-634">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-634">Int16</span></span>|  
|<span data-ttu-id="28ec4-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="28ec4-636">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-636">String</span></span>|  
|<span data-ttu-id="28ec4-637">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-637">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-638">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-638">String</span></span>|  
|<span data-ttu-id="28ec4-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="28ec4-639">DATE_CREATED</span></span>|<span data-ttu-id="28ec4-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-640">DateTime</span></span>|  
|<span data-ttu-id="28ec4-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="28ec4-641">DATE_MODIFIED</span></span>|<span data-ttu-id="28ec4-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="28ec4-643">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="28ec4-643">Views</span></span>  
  
|<span data-ttu-id="28ec4-644">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-644">ColumnName</span></span>|<span data-ttu-id="28ec4-645">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-646">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-647">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-647">String</span></span>|  
|<span data-ttu-id="28ec4-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-649">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-649">String</span></span>|  
|<span data-ttu-id="28ec4-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-650">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-651">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-651">String</span></span>|  
|<span data-ttu-id="28ec4-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="28ec4-653">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-653">String</span></span>|  
|<span data-ttu-id="28ec4-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="28ec4-654">CHECK_OPTION</span></span>|<span data-ttu-id="28ec4-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-655">Boolean</span></span>|  
|<span data-ttu-id="28ec4-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="28ec4-656">IS_UPDATABLE</span></span>|<span data-ttu-id="28ec4-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-657">Boolean</span></span>|  
|<span data-ttu-id="28ec4-658">POPIS</span><span class="sxs-lookup"><span data-stu-id="28ec4-658">DESCRIPTION</span></span>|<span data-ttu-id="28ec4-659">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-659">String</span></span>|  
|<span data-ttu-id="28ec4-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="28ec4-660">DATE_CREATED</span></span>|<span data-ttu-id="28ec4-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-661">DateTime</span></span>|  
|<span data-ttu-id="28ec4-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="28ec4-662">DATE_MODIFIED</span></span>|<span data-ttu-id="28ec4-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="28ec4-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="28ec4-664">Indexy</span><span class="sxs-lookup"><span data-stu-id="28ec4-664">Indexes</span></span>  
  
|<span data-ttu-id="28ec4-665">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="28ec4-665">ColumnName</span></span>|<span data-ttu-id="28ec4-666">DataType</span><span class="sxs-lookup"><span data-stu-id="28ec4-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="28ec4-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-667">TABLE_CATALOG</span></span>|<span data-ttu-id="28ec4-668">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-668">String</span></span>|  
|<span data-ttu-id="28ec4-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="28ec4-670">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-670">String</span></span>|  
|<span data-ttu-id="28ec4-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-671">TABLE_NAME</span></span>|<span data-ttu-id="28ec4-672">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-672">String</span></span>|  
|<span data-ttu-id="28ec4-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="28ec4-673">INDEX_CATALOG</span></span>|<span data-ttu-id="28ec4-674">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-674">String</span></span>|  
|<span data-ttu-id="28ec4-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="28ec4-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="28ec4-676">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-676">String</span></span>|  
|<span data-ttu-id="28ec4-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-677">INDEX_NAME</span></span>|<span data-ttu-id="28ec4-678">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-678">String</span></span>|  
|<span data-ttu-id="28ec4-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="28ec4-679">PRIMARY_KEY</span></span>|<span data-ttu-id="28ec4-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-680">Boolean</span></span>|  
|<span data-ttu-id="28ec4-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="28ec4-681">UNIQUE</span></span>|<span data-ttu-id="28ec4-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-682">Boolean</span></span>|  
|<span data-ttu-id="28ec4-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="28ec4-683">CLUSTERED</span></span>|<span data-ttu-id="28ec4-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-684">Boolean</span></span>|  
|<span data-ttu-id="28ec4-685">TYP</span><span class="sxs-lookup"><span data-stu-id="28ec4-685">TYPE</span></span>|<span data-ttu-id="28ec4-686">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-686">Int32</span></span>|  
|<span data-ttu-id="28ec4-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="28ec4-687">FILL_FACTOR</span></span>|<span data-ttu-id="28ec4-688">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-688">Int32</span></span>|  
|<span data-ttu-id="28ec4-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="28ec4-689">INITIAL_SIZE</span></span>|<span data-ttu-id="28ec4-690">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-690">Int32</span></span>|  
|<span data-ttu-id="28ec4-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="28ec4-691">NULLS</span></span>|<span data-ttu-id="28ec4-692">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-692">Int32</span></span>|  
|<span data-ttu-id="28ec4-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="28ec4-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="28ec4-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-694">Boolean</span></span>|  
|<span data-ttu-id="28ec4-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="28ec4-695">AUTO_UPDATE</span></span>|<span data-ttu-id="28ec4-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-696">Boolean</span></span>|  
|<span data-ttu-id="28ec4-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="28ec4-697">NULL_COLLATION</span></span>|<span data-ttu-id="28ec4-698">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-698">Int32</span></span>|  
|<span data-ttu-id="28ec4-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="28ec4-700">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-700">Int64</span></span>|  
|<span data-ttu-id="28ec4-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="28ec4-701">COLUMN_NAME</span></span>|<span data-ttu-id="28ec4-702">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-702">String</span></span>|  
|<span data-ttu-id="28ec4-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="28ec4-703">COLUMN_GUID</span></span>|<span data-ttu-id="28ec4-704">Guid</span><span class="sxs-lookup"><span data-stu-id="28ec4-704">Guid</span></span>|  
|<span data-ttu-id="28ec4-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="28ec4-705">COLUMN_PROPID</span></span>|<span data-ttu-id="28ec4-706">Int64</span><span class="sxs-lookup"><span data-stu-id="28ec4-706">Int64</span></span>|  
|<span data-ttu-id="28ec4-707">KOLACE</span><span class="sxs-lookup"><span data-stu-id="28ec4-707">COLLATION</span></span>|<span data-ttu-id="28ec4-708">Int16</span><span class="sxs-lookup"><span data-stu-id="28ec4-708">Int16</span></span>|  
|<span data-ttu-id="28ec4-709">KARDINALITA</span><span class="sxs-lookup"><span data-stu-id="28ec4-709">CARDINALITY</span></span>|<span data-ttu-id="28ec4-710">Desetinné číslo</span><span class="sxs-lookup"><span data-stu-id="28ec4-710">Decimal</span></span>|  
|<span data-ttu-id="28ec4-711">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="28ec4-711">PAGES</span></span>|<span data-ttu-id="28ec4-712">Int32</span><span class="sxs-lookup"><span data-stu-id="28ec4-712">Int32</span></span>|  
|<span data-ttu-id="28ec4-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="28ec4-713">FILTER_CONDITION</span></span>|<span data-ttu-id="28ec4-714">String</span><span class="sxs-lookup"><span data-stu-id="28ec4-714">String</span></span>|  
|<span data-ttu-id="28ec4-715">INTEGROVANÉ</span><span class="sxs-lookup"><span data-stu-id="28ec4-715">INTEGRATED</span></span>|<span data-ttu-id="28ec4-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="28ec4-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28ec4-717">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28ec4-717">See also</span></span>

- [<span data-ttu-id="28ec4-718">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="28ec4-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
