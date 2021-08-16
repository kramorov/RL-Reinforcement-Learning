# RL-Reinforcement-Learning
# Обучение с подкреплением
## Целью написания этой статьи является коротко рассказать об обучении с подкреплением, дать описание англоязычным терминам, используемым в RL, в том значении, как они используются в функциональном API TensorFlow.

Главными действующими лицами в RL являются агент (agent) и среда (environment). Среда - это мир, где обитает агент и с которой он взаимодействует. Взаимодействие осуществляется пошагово. На каждом шаге агент видит наблюдение (observation) или состояние (state) среды, и принимает решение, какое действие (action) предпринять. Выполняя наблюдение (observation), агент не всегда может видеть состояние среды или среду целиком. Скажем, в карточной игре, агент не может видеть карты соперника или карты в колоде. Если использоовать эту аналогию, то средой (environment) будут карты на руках у игроков и в колоде, а наблюдением (observation) агента - только карты, которые вскрыты. Продолжая аналогию карточной игры, шаг игры состоит из ходов игроков. После каждого хода меняется состояние (state) среды, и меняется наблюдение игрока. Таким образом, среда, состояние среды может меняться как под воздействием игрока, так и без его участия.

Агент получает сигнал от среды в виде вознаграждения или награды (reward). Русский перевод этого термина не точно воспроизводит смысл этого термина. Reward в терминах RL может быть как наградой (поощрением), так и наказанием (депремированием). В дальнейшем на русском я буду использовать слово "награда". Награда представляет собой некоторое число, которое показывает результат действий агента. Награда выдается средой не на каждом шаге, а только при каком-то изменении среды. Например, в пиг-понге, футболе и т.п. это гол. В карточной игре - завершение очередного розыгрыша. В гонках - столкновение с препятствием или поднятие бонуса (канистра, шина и т.п.).

Целью агента является максимизировать суммарное количество наград за какой-то промежуток времени (сет в теннисе, партия в шашках, продержаться 50 секунд в бою и т.п.). Суммарное количество наград назовем "результат" (return).

Целью обучения с подкреплением является обучение агента такому поведению, чтобы результат был максимальный.

Сначала обсудим термины, используемые в RL:
Состояния  и наблюдения (states and observations);
Пространство действий (action space);
Политики (policies);
Траектории (trajectories);
different formulations of return,
the RL optimization problem,
and value functions.
States and Observations
A state s is a complete description of the state of the world. There is no information about the world which is hidden from the state. An observation o is a partial description of a state, which may omit information.

In deep RL, we almost always represent states and observations by a real-valued vector, matrix, or higher-order tensor. For instance, a visual observation could be represented by the RGB matrix of its pixel values; the state of a robot might be represented by its joint angles and velocities.

When the agent is able to observe the complete state of the environment, we say that the environment is fully observed. When the agent can only see a partial observation, we say that the environment is partially observed.
