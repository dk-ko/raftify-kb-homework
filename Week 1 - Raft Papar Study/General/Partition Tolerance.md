**Partition Tolerance**(파티션 허용성)는 분산 시스템의 **CAP 정리**에서 등장하는 세 가지 속성 중 하나로, 시스템이 네트워크 분할(Partition) 상태에서도 정상적으로 작동할 수 있는 능력을 의미합니다.

### 네트워크 분할(Partition)이란?

- **네트워크 분할**은 분산 시스템에서 네트워크가 여러 부분으로 나누어져, 이들 부분 사이의 통신이 불가능한 상태를 의미합니다.
- 예를 들어, 네트워크 중간에 있는 라우터가 고장 나서 네트워크를 두 개의 서로 연결되지 않은 부분으로 나누는 상황을 생각할 수 있습니다.
- 이 상황에서 분산 시스템의 노드들은 일부만 서로 통신할 수 있으며, 전체 네트워크의 일관성을 유지하는 것이 어려워집니다.

### Partition Tolerance의 의미

- **파티션 허용성**은 분산 시스템이 이러한 네트워크 분할 상황에서도 부분적인 기능을 유지하거나, 파티션이 복구될 때까지 시스템의 일관성을 유지하는 능력을 의미합니다.
- 시스템이 파티션 허용성을 갖추려면, 네트워크 분할 중에도 데이터 손실이나 심각한 불일치가 발생하지 않도록 설계되어야 합니다.

### CAP 정리와 파티션 허용성

- **CAP 정리**는 분산 시스템이 세 가지 속성(Consistency, Availability, Partition Tolerance) 중에서 두 가지만 동시에 만족할 수 있다는 것을 설명합니다.
  - **일관성(Consistency)**: 모든 노드가 같은 시점에 동일한 데이터를 가집니다.
  - **가용성(Availability)**: 모든 요청이 성공 또는 실패 응답을 즉시 반환합니다.
  - **파티션 허용성(Partition Tolerance)**: 네트워크가 분할된 상태에서도 시스템이 정상적으로 동작합니다.

- CAP 정리에 따르면, 파티션 허용성을 포기할 수 없는 상황에서는 시스템 설계자가 **일관성**과 **가용성** 사이에서 트레이드오프를 해야 합니다.
  - **CP 시스템**: 일관성과 파티션 허용성을 보장하지만, 가용성을 포기합니다. (예: 네트워크 분할 시 일부 노드에 접근할 수 없도록 하여 데이터 일관성을 유지)
  - **AP 시스템**: 가용성과 파티션 허용성을 보장하지만, 일관성을 포기합니다. (예: 네트워크 분할 시 각 파티션에서 독립적으로 데이터를 처리하므로 일관성이 깨질 수 있음)

### 파티션 허용성의 구현 예시

- **분산 데이터베이스**:
  - Cassandra와 같은 분산 데이터베이스는 파티션 허용성을 제공하며, 네트워크 분할 시 각 파티션이 독립적으로 작동하면서도 가능한 빨리 일관성을 회복합니다.
  - 이 경우, 시스템은 가용성을 유지하면서 일관성을 포기하거나 약한 일관성을 제공하게 됩니다.

- **분산 파일 시스템**:
  - Google의 Spanner와 같은 시스템은 파티션 허용성을 유지하면서도 글로벌하게 일관된 데이터를 제공하도록 설계되어 있습니다. 이를 위해 복잡한 시계 동기화와 리더-팔로워 구조를 사용합니다.

### 결론

파티션 허용성은 분산 시스템에서 네트워크 분할과 같은 예기치 못한 상황에서 시스템이 계속해서 작동할 수 있도록 하는 중요한 속성입니다. 그러나 이를 유지하려면 일관성이나 가용성 중 하나를 포기해야 하는 트레이드오프가 존재합니다. 따라서, 분산 시스템 설계자는 시스템의 목적과 요구사항에 맞게 이러한 속성들을 균형 있게 고려해야 합니다.

